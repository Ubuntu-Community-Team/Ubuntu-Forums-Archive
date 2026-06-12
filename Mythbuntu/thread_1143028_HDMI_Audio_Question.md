---
title: "HDMI Audio Question"
date: 2009-04-29
forum: Mythbuntu
---

### Post by wcunnin3 on 2009-04-29
I set up an .asoundrc file in my home directory to provide HDMI sound out from my GA-E7AUM-SH motherboard using Mythbuntu 9.04.  In my .asoundrc, I used the following:

```
pcm.!default hdmi:NVidia
```

I set Myth to use ALSA:hdmi, which produces HDMI sound to my receiver with no problems.  However, when I try to open a video file with mplayer from the desktop, I get no sound.  I also get a snd_ctl_failed error.

Frankly, I am disinclined to mess with things, as it works now, but I am curious as to why it has happened like this.  With 9.04 beta, I used a much more complicated asound.conf file that did the trick, though my receiver did not show Dolby Digital signals when playing OTA HD broadcasts when it should have.  I tried using this in my 9.04 release, but it did not work.  Here's the asound.conf:

```

pcm.!default {
        type plug
        slave {
                pcm multi
                rate 48000
        }
        ttable.0.0 1.0
        ttable.1.1 1.0
        ttable.0.2 1.0
        ttable.1.3 1.0
}

ctl.!default hdmiout

pcm.optical {
        type hw
        card 0
        device 1
}

ctl.optical {
        type hw
        card 0
        device 1
}

pcm.hdmiout {
        type hw
        card 0
        device 3
}

ctl.hdmiout {
        type hw
        card 0
        device 3
}

pcm.multi {
        type multi
        slaves.a.pcm "hdmiout"
        slaves.a.channels 2
        slaves.b.pcm "optical"
        slaves.b.channels 2

        bindings.0.slave a
        bindings.0.channel 0
        bindings.1.slave a
        bindings.1.channel 1

        bindings.2.slave b
        bindings.2.channel 0
        bindings.3.slave b
        bindings.3.channel 1
}

ctl.multi {
        type hw
        card 0
}

```

Any thoughts?

---

### Post by Dewey_Oxberger on 2009-04-30
>Any thoughts?

I rarely think.  It's bad for the brain.

1) Why all the ctl definitions.  I don't think they really get used any more.

2) Why the multi?  You are just doing audio over hdmi right?

Here is an example audio over hdmi asound.conf I did a while back.  It creates a virtual device called hdmi_complete that gives mythtv the ability to send the audio over hdmi and control the volume.  I tried to make the simplest set of virtual devices that would get the job done.  Once hdmi_complete is done I make it default.

```
# HDMI configuration with volume control for MythTV
# For ALSA 1.0.19  - 1/31/2009

# Instructions for use
# 1) Find your hmdi hardware Card Number and Device Number.  Open a terminal and do:
#    aplay -L
#    That will list all of the hardware audio devices.  Look for the one labeled HDMI.
#    Note what Card Number and Device Number it lists (they seem to be card 0,
#    device 3 but your system may be different).
# 2) Edit the pcm.hdmi_hw device defined here to set your Card Number and Device Number.
# 3) Put this file in either /etc/asound.conf or in your home directory as .asoundrc.
#    sudo cp jons_asound.conf /etc/asound.conf
#      or
#    sudo cp jons_asound.conf $HOME/.asound.conf
# 4) Exit mythfrontend.  Then restart the sound system:
#    sudo /etc/init.d/alsa-utils restart
# 5) Start mythfrontend and go to the audio setup screen
#    "Utilities / Setup"  then "Setup" then "General" then "Next" until you
#    get to the Audio tab.
# 6) Fill in the info - it's case sensitive:
#    Audio output device: ALSA:hdmi_complete     <--- note you have to type in this field
#    Passthrough output devide: Default
#     ... Stereo... ... Passive...
#    Mixer Device: ALSA:default
#    Mixer controls: hdmi_volume                 <--- type in this field
# 7) Work your way back to Watch TV and give it a try.

pcm.hdmi_hw {
  type hw
  card 0     #  <-----  Put your card number here
  device 3   #  <-----  Put your device number here
}

pcm.hdmi_formatted {
  type plug
  slave {
    pcm hdmi_hw
    rate 48000
    channels 2
  }
}

pcm.hdmi_complete {
  type softvol
  slave.pcm hdmi_formatted
  control.name hdmi_volume
  control.card 0
}

pcm.!default hdmi_complete
 
```

You might try cutting your asound.rc file down to the smallest set of stuff you need.

---

### Post by wcunnin3 on 2009-04-30
1.  I don't have an explanation for all of the ctl and pcm stuff in that bigger asound.conf file.  I was OK using only that first line: ```
pcm.!default hdmi:NVidia
```
instead of the bigger, more complicated conf file.


2.  I tried using your .asoundrc, and it worked right out of the box (except that my mp3's won't play).  I noticed that my mp3's wouldn't play with my original .asoundrc either.  That's a small price to pay when now I have sound in flash, as well.

3.  I'm not sure I understand why such similar things do and do not work between these conf files.

Thanks,
-Will

---

### Post by kilowhisky on 2009-04-30
So this allows for pcm and digital through HDMI?  How stable is it?

---

### Post by wcunnin3 on 2009-05-02
Well, I get audio over my HDMI cable for everything except music in Myth (works in VLC on the desktop).  I find it to be very stable, although the only nag is you can't have two things going at once.  For instance, if you have a flash page open, that will be the only thing that produces sound.  If you switch back to a different flash page or to Myth, no sound comes out of those.

As to PCM, I don't quite know.  My receiver shows Dolby when that is coming down the line from OTA signals.  It doesn't show multichannel when playing a movie file with AC3, although I still get the surround sound.

---

### Post by tobiz on 2009-05-02
> **wcunnin3 said:**
> Well, I get audio over my HDMI cable for everything except music in Myth (works in VLC on the desktop).  I find it to be very stable, although the only nag is you can't have two things going at once.  For instance, if you have a flash page open, that will be the only thing that produces sound.  If you switch back to a different flash page or to Myth, no sound comes out of those.

As to PCM, I don't quite know.  My receiver shows Dolby when that is coming down the line from OTA signals.  It doesn't show multichannel when playing a movie file with AC3, although I still get the surround sound.
Same here, I get HDMI audio for all video sources including OTA HD, via MythTV, vlc,xine, mplayer etc but not from MythMusic. But I do get music over HDMI from amarok - not been able to explain this, just assume it's some strange MythMusic config.

---

### Post by Dewey_Oxberger on 2009-05-02
The asound.conf I made creates three (or so) virtual devices.  I'd guess that the music player was looking for some specific device.  The device it needs may be specified on it's command line (or you can probably override it with a command line option).  I'm fairly sure mine works - I'll have a look and post back.

---

### Post by joshoekstra on 2009-05-07
I'm using the GA-E7AUM-DS2H as well and got HDMI to TV working as well, I however like to drive the analog-receiver connected to audio-ports on the motherboard at the same time.
Is this possible and how do I set up a asound.conf for that?

---

### Post by Dewey_Oxberger on 2009-05-07
With ALSA everything is possible ;)

You'll need to read the ALSA docs.  You create another virtual device that does a multi or slave.  You tell alsa to send the audio out multiple devices.

I know there are examples on the web so google alsa analog spdif.

---

