---
title: "How to restore Internal Channel Changing??"
date: 2010-11-23
forum: Mythbuntu
---

### Post by kyphos on 2010-11-23
I have a working 10.04 Mythbuntu system, using a PVR-150 tuner card. The PVR-150 is configured with two inputs: a coax from my analog cable feed, and an S-Video input from a 'static' video source.  No IR blasters or remote channel changing is involved.

All has been working well, except that the audio levels between the two video inputs are quite different. Recordings made from the S-video input have very low audio, and we have to crank the TV volume to the max in order to hear anything.   Thanks to helpful posts on this forum and elsewhere, I figured out how to use the External Channel Change command (as defined in mythbackend's Input Connections) to override the default volume settings. I created a couple of scripts to invoke v4l2-ctl and send new volume settings to the PVR-150, one script for each input. (for good measure, I also tweaked the video saturation and brightness settings to get more consistent picture quality).

**My problem is that the internal channel change function no longer works.** The tuner input on the PVR-150 is now stuck on channel 2.  If I run LiveTV and try to change the channel, the OPG indicates that a new channel is being selected, but the video doesn't change. 

My guess is that the presence of the External Channel Change Command is disabling MythTV's internal channel changer.  If so, can I embed something inside my external command script that will invoke the system's channel changer??

Or perhaps it's a timing conflict: my script might be sending control settings to the tuner card at the same time that the internal channel changer is trying to send the channel-change command. 

Here is one of the scripts I'm using to fiddle the audio/video parameters. I've never written a script before so I'm sure there is room for improvement. The logging I put in indicates that it is working as intended.

```
#!/bin/bash
# /usr/local/bin set_svid_ctrls.sh
# script to set control parameters for S-Vid input on PVR-150

DEVICE="-d /dev/video-PVR150"

exec >>/var/log/mythtv/set_tuner.log 2>&1

echo "called for S-vid input"
echo Settings before:
v4l2-ctl $DEVICE -l | head -8 | tail -5

#control settings
B=150  #picture brightness (0-255)
S=40   #saturation (0-127)
V=65000 #volume (0-65535)

v4l2-ctl $DEVICE --set-ctrl brightness=$B,saturation=$S,volume=$V >/dev/null

#kick the audio input for good measure (tinny audio problem)
v4l2-ctl $DEVICE --set-audio-input=1 >/dev/null

echo ;echo Settings after:
v4l2-ctl $DEVICE -l | head -8 | tail -5
echo ====================
```

---

### Post by tgm4883 on 2010-11-23
Thats correct the external channel change command is disabling it. IIRC, You can use v4l2-ctl to change the channel on the PVR-150, but I haven't used my PVR-150 in almost 2 years so I'm a little rusty on that

---

### Post by kyphos on 2010-11-23
> **tgm4883 said:**
> Thats correct the external channel change command is disabling it. IIRC, You can use v4l2-ctl to change the channel on the PVR-150, but I haven't used my PVR-150 in almost 2 years so I'm a little rusty on that

Damn, I was afraid of that. Unfortunately, v4l2-ctl doesn't deal in channel numbers but in frequencies  
     >v4l2-ctl   --set-freq=<freq>

So if I want my script to take over channel changing duties, I think it would have to convert channel numbers into the corresponding frequencies.  No doubt, that mapping is stored in the mysql database somewhere, but that's way beyond my scripting capability.

Is there any chance I can invoke myth's internal channel changer routine from my external script, or am I SOL?  

Alternately, does anyone know where Myth stores the control values (volume, brightness, etc) that it stuffs into the tuner card?  I've looked high and low but haven't been able to find them.

Thanks.

---

### Post by kyphos on 2010-11-23
ivtv-tune might do what I need. Time to go play..

```
Usage: ivtv-tune [OPTIONS]...

  -h, --help              Print help and exit
  -V, --version           Print version and exit
  -c, --channel=CHANNEL   set new channel
  -d, --device=DEVICE     set video device node
  -f, --frequency=FREQ    set new frequency (MHz)
  -l, --list-channels     list all channels and their frequencies  
                            (default=off)
  -L, --list-freqtable    list all available frequency mappings  (default=off)
  -t, --freqtable=STRING  set frequency map to use
  -x, --xawtv=CHANNEL     set new channel using custom map from ~/.xawtv
```

---

### Post by kyphos on 2010-11-23
Good news - Bad news:

I am pleased to report that the ivtv-tune routine can be used to tune the desired channel. Thus, my external channel change script will both set the specfied channel (passed to it as $1 from the mythbackend) and also change the volume, brightness, saturation, etc settings.

But after the script changes the PVR-150 settings to what I want, something in mythbackend changes them back. As a result, my recordings get made using the parameters myth has stored somewhere.  Where can they be??

For the benefit of anyone wanting ideas on how to use an external change channel command to change the channel on an ivtv tuner card, my current script is below. But note that the various adjustments performed by the --set-ctrl line are not sticky. Some process in Myth overrides them immediately after the command script sets them.

```
#!/bin/bash
# script to set control parameters for tuner input on PVR-150
# also changes the channel using ivtv-tune, since the presence of this script
# in Input Connections config disables the internal channel changer

DEVICE="-d /dev/video-PVR150"

exec >>/var/log/mythtv/set_tuner.log 2>&1

echo "called for PVR-150 tuner1 input. Setting channel to $1"
ivtv-tune $DEVICE -c $1

echo Settings before:
v4l2-ctl $DEVICE -l | head -8 | tail -5

#control settings
B=130  #picture brightness (0-255) Myth default=127
S=63  #saturation (0-127) Myth default=63
V=62000 #volume (0-65535) Myth default =58880

v4l2-ctl $DEVICE --set-ctrl brightness=$B,saturation=$S,volume=$V >/dev/null

# kick the audio input for good measure
#v4l2-ctl $DEVICE --set-audio-input=0 >/dev/null

echo ;echo Settings after:
v4l2-ctl $DEVICE -l | head -8 | tail -5
echo =========================
```

---

