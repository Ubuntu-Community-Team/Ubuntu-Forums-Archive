---
title: "Please help getting Harmony 900 working with Mythtv..."
date: 2010-03-28
forum: Mythbuntu
---

### Post by killabee44 on 2010-03-28
Guys,

I am running mythbuntu 9.10 and MediaGate HA-IR01SV Media Center IR receiver.

For some time now I have been trying to get my Harmony 900 working with Myth. I followed a guide here:

[http://www.mythtvtalk.com/forum/hardware/7871-biggest-baddest-best-remote-control.html](http://www.mythtvtalk.com/forum/hardware/7871-biggest-baddest-best-remote-control.html)

In this guide you use the logitech web interface and program the 900 to use the buttons of a Sony receiver (because it has more buttons). 

Others have been successful getting this setup to work with lircd and lircrc files posted at that link. I have not and am trying to figure out why.

I think I am doing something wrong somewhere and the problem might be because of how I am using the Myth controll center > Infrared section. 

so, my question is:

**If I am using my own lircd and lircrc files, how exatly do I configure myth controll center?**

Also, in order to troubleshoot this, what commands, logs, etc to I look at?

Thanks.

---

### Post by phroman on 2010-03-29
Hi killabee44, why don't you post your /etc/lirc/hardware.conf and /et/lirc/lirc.conf files to start with.  I'll read more on the link you posted in the mean time.

---

### Post by killabee44 on 2010-03-30
> **phroman said:**
> Hi killabee44, why don't you post your /etc/lirc/hardware.conf and /et/lirc/lirc.conf files to start with.  I'll read more on the link you posted in the mean time.

Phroman,

Here is my /etc/lirc/harware.conf:
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES=""
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Direct TV Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_mceusb2"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD="" 
```

And here is my etc/lirc/lircd.conf:

```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.3-CVS(default) on Sun Aug 10 22:04:27 2008
#
# contributed by 
#
# brand:                       Sony STR-DA5300ES
# model no. of remote control: Sony RM-AAL008
# devices being controlled by this remote:
#
# This file is specifically designed for the Harmony 880
# universal remote control.  The Harmony 880 must be configured
# to emulate the remote control for a specific device.  The
# Sony STR-DA5300ES receiver was chosen because it has a large
# number of buttons, allowing many additional buttons on the
# Harmony 880 to be configured, for maximum flexibility.
#
# The Harmony configuration for this device also includes some
# additional buttons, such as InputHdmi 1-6, but their codes have a
# different length or something, so they can't be learned without
# using irrecord in raw mode.  Those buttons are not included here.
#
# To help create a corresponding lircrc file, the first set of codes
# has a sample mapping to the standard buttons on the Harmony 880
# remote control.
#

begin remote

  name  sony-str-da5300es
  bits           15
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          256

  header       2477   640
  one          1343   640
  zero          659   640
  gap          46882
  toggle_bit_mask 0x0

      begin codes
# Standard button "Mute".
          Mute                     0x140C

# Standard button "Volume Up".
          VolumeUp                 0x240C

# Standard button "Volume Down".
          VolumeDown               0x640C

# Standard button "Down Arrow".
          ModeDown                 0x7B0D

# Standard button "Up Arrow".
          ModeUp                   0x3B0D

# Standard button "Channel Down".
          PresetPrev               0x440C

# Standard button "Channel Up".
          PresetNext               0x040C

# Standard button "Prev".
          AmFmToggle               0x78B4

# Standard button "Up".
          DirectionUp              0x0F0D

# Standard button "Down".
          DirectionDown            0x4F0D

# Standard button "Left".
          DirectionLeft            0x2F0D

# Standard button "Right".
          DirectionRight           0x6F0D

# Standard button "OK".
          Select                   0x180C

# Standard button "Menu".
          Menu                     0x770D

# Standard button "Exit".
          PowerOff                 0x7A0C

# Standard button "Guide".
          OnScreen                 0x650C

# Standard button "Info".
          Display                  0x690C

# Standard button "Stop".
          Dimmer                   0x590C

# Standard button "Skip Back".
          BalanceLeft              0x320C

# Standard button "Skip Forward".
          BalanceRight             0x720C

# Standard button "Play".
          SndBckDecoding           0x310D

# Standard button "Record".
          SndFldsMovie             0x610D

# Standard button "Rewind".
          TuningDown               0x1A0D

# Standard button "Fast Forward".
          TuningUp                 0x6A0D

# Standard button "Pause".
          SndFldsMusic             0x490D

# Standard button "1".
          1                        0x00B4

# Standard button "2".
          2                        0x40B4

# Standard button "3".
          3                        0x20B4

# Standard button "4".
          4                        0x60B4

# Standard button "5".
          5                        0x10B4

# Standard button "6".
          6                        0x50B4

# Standard button "7".
          7                        0x30B4

# Standard button "8".
          8                        0x70B4

# Standard button "9".
          9                        0x08B4

# Standard button "Plus".
          TestTone                 0x290D

# Standard button "0".
          0                        0x48B4

# Standard button "E".
          Equalizer                0x190D

# Additional buttons.
          AacBilingual             0x740C
          AFD                      0x710D
          AnalogDirect             0x490C
          AudioSplit               0x130D
          BassBoost                0x590D
          DirectTune               0x0A0D
          EqualizerBassDown        0x450D
          EqualizerBassUp          0x050D
          EqualizerTrebleDown      0x750D
          EqualizerTrebleUp        0x350D
          Input5.1Ch               0x270C
          InputAM                  0x2C0C
          InputAux                 0x5C0C
          InputCD                  0x520C
          InputDM                  0x5F0C
          InputDVD                 0x5F0C
          InputFM                  0x0C0C
          InputLink                0x5C0D
          InputLd                  0x6B0C
          InputMd                  0x4B0C
          InputMode                0x060D
          InputPhono               0x020C
          InputSAT                 0x600D
          InputTape                0x620C
          InputTv                  0x2B0C
          InputVideo1              0x220C
          InputVideo2              0x3C0C
          InputVideo3              0x210C
          InputVideo4              0x610C
          InputVideo5              0x410C
          MenuDown                 0x170D
          MenuLeft                 0x270D
          MenuRight                0x670D
          MenuUp                   0x570D
          NightMode                0x020D
          Presets                  0x320D
          PresetShift              0x470D
          Sleep                    0x030C
          Stereo                   0x410D
          SurroundNormal           0x210D

      end codes

end remote
```

---

### Post by phroman on 2010-03-30
Hey killabee44, so your /etc/lirc/hardware.conf file, which tells lirc what your physical remote control and transmitter devices are, doesn't have a remote listed, so it can't receive any signals.  Make a copy of your /etc/lirc/lircd.conf file.  Run mythcontrol center, choose infrared, enable remote and see if your remote is listed.  If it is, select it, and do the same for a transmitter.  If it does have either of those, post back the hardware.conf and lircd.conf files.  I'm up for a while.  Phroman.

---

### Post by killabee44 on 2010-03-30
> **phroman said:**
> Hey killabee44, so your /etc/lirc/hardware.conf file, which tells lirc what your physical remote control and transmitter devices are, doesn't have a remote listed, so it can't receive any signals.  Make a copy of your /etc/lirc/lircd.conf file.  Run mythcontrol center, choose infrared, enable remote and see if your remote is listed.  If it is, select it, and do the same for a transmitter.  If it does have either of those, post back the hardware.conf and lircd.conf files.  I'm up for a while.  Phroman.

Yep, I tried that before... the remote is not listed. The ir receiver is listed and I read somewhere to choose the "Microsoft Windows Media Center V2 (usb) : Direct TV Receiver"  for an MCE receiver or generic MCE receiver.

The problem must be the remote.

---

### Post by phroman on 2010-03-30
Ok, does it list the exact ir receiver you have?  I think the ir receiver is the remote, so that's good, that will make us a good hardware.conf file we can work with.  Go back and select the ir receiver, then post your hardware.conf file.

---

### Post by killabee44 on 2010-03-31
> **phroman said:**
> Ok, does it list the exact ir receiver you have?  I think the ir receiver is the remote, so that's good, that will make us a good hardware.conf file we can work with.  Go back and select the ir receiver, then post your hardware.conf file.



In the mythbuntu controllcentre there are two entries. The first thing you see is the entry for remote. I chose "no remote" since figured I would just configure the lircd.conf file with the Sony data and it would work. 

I also tried selecting a remote. The program generates an lircd.conf file for that specific remote. I then replaced the data in the lircd.conf file with the data for the Sony and it still did not work. 



The second entry is for the receiver only. The one I have is listed as: "Windows Media Center V2 (usb)" which is what I have read that you select for this specific generic mce receiver as and it will work. 

Could it be that the problem is that the remote is not listed in the hardware.conf, thus it thinks there is no remote at all (since I chose no remote in the mythbuntu controllcentre >infrared?

---

### Post by killabee44 on 2010-03-31
Now looking at the harware.conf file under the remote control part, what exactly should be listed for the Sony under those entries?

#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES=""
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""


I went ahead and just selected a Microsoft Media Center remote under the controllcentre and here is the hardware.conf that it generated (for the receiver I selected "microsoft windows media center v2", which is right):

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev lirc_mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Direct TV Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_mceusb2"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

---

### Post by phroman on 2010-03-31
> In the mythbuntu controllcentre there are two entries. The first thing you see is the entry for remote. I chose "no remote" since figured I would just configure the lircd.conf file with the Sony data and it would work.

It will probably need a small edit and won't work initially.

> I also tried selecting a remote. The program generates an lircd.conf file for that specific remote. I then replaced the data in the lircd.conf file with the data for the Sony and it still did not work

Same thing, it needs to be edited, not significantly, but it needs to be done.

I think we're having a terminology issue..  ;)
> The second entry is for the receiver only. The one I have is listed as: "Windows Media Center V2 (usb)" which is what I have read that you select for this specific generic mce receiver as and it will work.

The second entry is for a transmitter, a receiver is to receive the signals from the remote control.

> Could it be that the problem is that the remote is not listed in the hardware.conf, thus it thinks there is no remote at all (since I chose no remote in the mythbuntu controllcentre >infrared?

Exactly, but we can fix that.  If all you have is a remote control, and a usb receiver that came with it to receive that remote controls signals, you do not have any transmitting capability. You will need an additional cable to transmit.  So, to configure your remote control, go back and select your remote control in MCC, hopefully it lists the exact one, if not we can enter it manually.  Then post back with the hardware.conf and lircd.conf file it creates in that process, then we'll tweak that to work first.  Coolio?

Am I clear on the difference between remote control and transmitting?

---

### Post by killabee44 on 2010-03-31
> **phroman said:**
> It will probably need a small edit and won't work initially.



Same thing, it needs to be edited, not significantly, but it needs to be done.

I think we're having a terminology issue..  ;)


The second entry is for a transmitter, a receiver is to receive the signals from the remote control.



Exactly, but we can fix that.  If all you have is a remote control, and a usb receiver that came with it to receive that remote controls signals, you do not have any transmitting capability. You will need an additional cable to transmit.  So, to configure your remote control, go back and select your remote control in MCC, hopefully it lists the exact one, if not we can enter it manually.  Then post back with the hardware.conf and lircd.conf file it creates in that process, then we'll tweak that to work first.  Coolio?

Am I clear on the difference between remote control and transmitting?

The Remote control I am using is a Harmony 900 but the IR receiver is an MCE microsoft certified clone that works with a MCE remote control (or any remote control I guess), but Im not using the MCE remote control. 

I am using the Harmony which is emulating the Sony remote control (in order to get more buttons to use).

The problem is that the Sony is not listed in the Remotes  in MCC, which is why I was using the lircd with the Sony info. Like you said, I guess it just needs to be tweaked.

---

### Post by phroman on 2010-03-31
My fault, sorry bout that, I forgot in all of the mce/ir/lirc/transmitting mixupery, that you were using the harmony remote.  I don't think that'll be a problem, go to MCC, select the MCE remote, that should at least load the correct driver and/or module for the ir receiver that you're using, and we can tweak the rest of the files manually.

---

### Post by killabee44 on 2010-03-31
> **killabee44 said:**
> 

I went ahead and just selected a Microsoft Media Center remote under the controllcentre and here is the hardware.conf that it generated. For the receiver I selected "microsoft windows media center v2", which I know is right:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev lirc_mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Direct TV Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_mceusb2"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to p**** REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

Yes, the hardware.conf above is the one I generated after telling MCC that I had an MCE remote and MCE IR receiver. I just don't know how to adjust it to tell it that it's a Sony STR-DA5300ES remote (which is the signal that my Harmony remote is programmed to send).

---

### Post by phroman on 2010-03-31
Alright, I sincerely apologize if I'm missing something, but you keep referring to a receiver, and I think what you mean is a transmitter.  Just trying to get our terminology strait so we're on the same page and are talking about the same things.  This is important as a transmitter is a different piece of hardware, and confusing the two can lead to confusion.  And possibly cats falling from the sky.  Don't laugh, I've seen it. Does that make sense?

Ok, so in your hardware.conf file you need to change the name of the remote in this line:
```
REMOTE="Windows Media Center Transceivers/Remotes (all)"

```
Change just what's in the quotes to "harmonyremote", save the file. 

Now post your /etc/lirc/lircd.conf file.  Sorry, I should have asked you to to that too.  I've got about 2 hours before I have to go but we should have enough time.  In fact if you subscribe to this thread, you can have an email sent if anyone replies, maybe I can continue to help from the road.

---

### Post by phroman on 2010-03-31
The next thing to do is check the mythtv file in ~/.lirc/mythtv.  At the top is says:
```
begin
    remote = yourremote
```

Whatever is in the remote = field, must exactly match what's in the REMOTE= field in your /etc/lirc/hardware.conf file.  It must also be the same in your /etc/lirc/lircd.conf file.  If they aren't all exactly the same, it won't work.  But you'll see the lircd.conf and the mythv file doesn't put it in quotes.  If there are any spaces in it, I would fill them with underscores.

---

### Post by killabee44 on 2010-03-31
> **phroman said:**
> Alright, I sincerely apologize if I'm missing something, but you keep referring to a receiver, and I think what you mean is a transmitter.  Just trying to get our terminology strait so we're on the same page and are talking about the same things.  This is important as a transmitter is a different piece of hardware, and confusing the two can lead to confusion.  And possibly cats falling from the sky.  Don't laugh, I've seen it. Does that make sense?

Ok, so in your hardware.conf file you need to change the name of the remote in this line:
```
REMOTE="Windows Media Center Transceivers/Remotes (all)"

```
Change just what's in the quotes to "harmonyremote", save the file. 

Now post your /etc/lirc/lircd.conf file.  Sorry, I should have asked you to to that too.  I've got about 2 hours before I have to go but we should have enough time.  In fact if you subscribe to this thread, you can have an email sent if anyone replies, maybe I can continue to help from the road.

You are correct. I will refer to them as the remote and the IR. That way we'll both know what Im talking about. Remember though that I can't put in the Harmony remote. The Harmony is basically acting as a sony-str-da5300es remote. I will use that because the lircd.conf file I posted before is the one Im trying to get working and it specifies the sony-str-da5300es.



> **phroman said:**
> The next thing to do is check the mythtv file in ~/.lirc/mythtv.  At the top is says:
```
begin
    remote = yourremote
```

Whatever is in the remote = field, must exactly match what's in the REMOTE= field in your /etc/lirc/hardware.conf file.  It must also be the same in your /etc/lirc/lircd.conf file.  If they aren't all exactly the same, it won't work.  But you'll see the lircd.conf and the mythv file doesn't put it in quotes.  If there are any spaces in it, I would fill them with underscores.

I will make sure tonight when I get home and confirm what the lircrc and hardware.conf all say and post back. Thanks.

---

### Post by killabee44 on 2010-03-31
Ok, here are the system generated files by MCC for the MCE remote and IR:


/etc/lirc/hardware.conf:

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev lirc_mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Direct TV Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_mceusb2"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```


/etc/lirc/lircd.conf file:

```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"

#Configuration for the Microsoft Windows Media Center V2 (usb) : Direct TV Receiver transmitter:
include "/usr/share/lirc/extras/transmitters/directtv/general.conf"
```


~/.lirc/mythtv:

```
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu
begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Replay
    config = Q
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Skip
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Back
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = More
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Left
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = VolUp
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = VolDown
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Home
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = ChanDown
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = ChanUp
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = RecTV
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = One
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Two
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Three
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Four
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Five
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Six
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Seven
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Eight
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Nine
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Zero
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Hash
    config = D
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Enter
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 1250
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 1200
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 1200
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 1250
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 1250
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 1250
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 1250
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = left
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 700
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 1250
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = select
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 600
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6050
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 1200
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = info
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 1250
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = back
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 700
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 1200
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 1250
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = exit
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 1200
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = ch-
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 1250
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = ch+
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 6000
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = directtv
    prog = mythtv
    button = 650
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Rec
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Skipback
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Skipfwd
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Fwd
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Start
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Back
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = More
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Volup
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Voldown
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Chup
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Chdown
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Left
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Rectv
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Dvdmenu
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Enter
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = RecTV
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Back
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Left
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Hash
    config = D
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Replay
    config = Q
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Skip
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Forward
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = ChanDown
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = ChanUp
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = VolDown
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = VolUp
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = More
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Home
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Enter
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Nine
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Eight
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Seven
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Six
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Five
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Four
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Three
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Two
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = One
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Zero
    config = 0
    repeat = 0
    delay = 0
end
```

Now, to make it all work for the Sony remote? 

I also noticed that the mythtv file has the remote name first, which the lircrc I posted at the beginning of this thread for the Sony does not have. That's an easy fix. I don't know how to go about the other two. They referred to files residing somewhere else. Here they are:


/usr/share/lirc/extras/transmitters/directtv/general.conf:

```
#
# this config file was automatically generated
# using lirc-0.8.1-CVS-pvr150(default) on Thu Nov 23 11:12:04 2006
#
# contributed by Chris Jacobs
#
# brand: DirecTV HD20-100
# model no. of remote control: HD20-100
# devices being controlled by this remote: DirecTV HD20-100
#

begin remote

  name   directtv
  flags RAW_CODES
  eps            30
  aeps          100

  ptrail        613
  repeat     0     0
  gap    29767

      begin raw_codes

          name 1
             6000    1150    1250    1100     650     550
              650     550     650     550     650     500
              650    1150     650     550     650    1150
              600

          name 2
             6000    1100    1250    1150     650     550
              650     550     600     550     650     550
             1250     550     650     550    1200     550
              650

          name 3
             6000    1150    1250    1100     650     550
              650     550     650     550     650     550
             1200    1150     650     550    1250    1150
              600

          name 4
             6000    1150    1250    1150     650     500
              650     550     650     550     650    1150
              650     500     650     550    1250    1150
              650

          name 5
             6000    1150    1250    1100     650     550
              650     550     650     500     650    1150
              650    1150     650    1150     600     550
              650

          name 6
             6000    1150    1250    1150     650     500
              650     550     650     550     650    1150
             1200     550     650    1150     650    1150
              600

          name 7
             6000    1100    1250    1150     650     550
              650     500     650     550     650    1150
             1250    1100     650    1150    1250     550
              650

          name 8
             6000    1150    1250    1100     650     550
              650     550     650     550    1200     550
              650     550     650    1150    1200     550
              650

          name 9
             6000    1100    1300    1100     650     550
              650     550     650     500    1250     550
              650    1150     650    1150    1200    1150
              650

          name 0
             6000    1150    1250    1150     650     500
              650     550     650    1150     650     550
              650    1100     650    1150    1250     550
              650

          name dash
             6000    1100    1300    1100     650     550
              650     550     650    1100     650     550
             1250     550     650    1100    1250    1150
              650

          name last
             6000    1100    1300    1100     650     550
              650     550     650     500    1250    1150
             1250    1150    1200    1150     650     550
              650

          name guide
             6000    1100    1300    1100     650     550
              650     550    1250     500    1250     550
              650     550     650     550     600     550
              650

          name up
             6000    1100    1300    1100     650     550
              650     550    1250     500     650     550
              650    1150    1250     500    1250    1150
              650

          name down
             6000    1150    1250    1100     650     550
              650     550    1250     500     650     550
             1250     550    1250    1150     600     550
              650

          name left
             6000    1150    1250    1150     650     500
              700     500    1250     550     650     550
             1250    1100    1250    1150     650    1150
              600

          name right
             6000    1150    1250    1100     650     550
              650     550    1250     500     650    1150
              650     550    1250    1100     650    1150
              650

          name select
             6000    1150    1250    1100     700     500
              650     550    1250     550     650    1100
              650    1150    1250    1150    1200     550
              650

          name action
             6000    1150    1250    1150     650     500
              650     550    1250     550    1250     550
              600    1150     650     550     650    1150
              650

          name list
             6050    1100    1250    1150     650     500
              650     550    1250     550    1250     550
             1200     550     650     550    1250     550
              650

          name info
             6000    1100    1250    1150     650     550
              650     500    1250     550    1250    1150
             1250     500     650    1150     650    1150
              650

          name back
             6000    1150    1250    1150     650     500
              700     500    1250     550     650    1150
             1200    1150     650     550     650     550
              650

          name power
             6000    1150    1250    1100     650     550
             1250     550     650     550     650     500
              650     550    1250    1150    1250     500
              650

          name exit
             6000    1150    1250    1150     650     500
              650     550    1250     550     650    1150
             1200     550    1250    1150    1250    1100
              650

          name ch-
             6000    1100    1250    1150     650     550
              650     500     650     550    1250    1150
             1250     550    1200     550    1250    1150
              650

          name ch+
             6000    1100    1300    1100     650     550
              650     500     700     500    1250    1150
              650    1150    1200     550    1250     550
              650

      end raw_codes

end remote
```


/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:

```
#
# brand:                        HP 
# model no. of remote control:  TSGH-IR01
# devices being controlled by this remote: HP Slimline S3100y
#
# RC-6 config file
#
# source: http://home.hccnet.nl/m.majoor/projects_remote_control.htm
#         http://home.hccnet.nl/m.majoor/pronto.pdf
#
# used by: Philips
#
#########
#
# Philips Media Center Edition remote control
# For use with the USB MCE ir receiver
#
# Dan Conti  dconti|acm.wwu.edu
#
# Updated with codes for MCE 2005 Remote additional buttons
# *, #, Teletext, Red, Green, Yellow & Blue Buttons
# Note: TV power button transmits no code until programmed.
# Updated 12th September 2005
# Graham Auld - mce|graham.auld.me.uk
#
# Radio, Print, RecTV are only available on the HP Media Center remote control
#
#
# Updated with codes for MCE 2007 Remote additional buttons
# Visualization, Aspect, SlideShow, Eject
# Note: 
# Renamed some buttons: DVD->DVDMenu, More->MoreInfo, Star->Asterisk, Hash->Pound
# Note: 
# Blue, Yellow, Green, Red, and Teletext buttons do not exist on the HP remote

begin remote

  name        mceusb
  bits                 16
  flags  RC6|CONST_LENGTH
  eps                  30
  aeps                100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits        21
  pre_data        0x37FF0
  gap              105000
  toggle_bit           22
  rc6_mask    0x100000000


      begin codes

#unused by HP remote
	Blue	      0x00007ba1
	Yellow	      0x00007ba2
	Green	      0x00007ba3
	Red	      0x00007ba4
	Teletext      0x00007ba5

#ba6 - bae unused 
        BA6           0x00007ba6
        BA7           0x00007ba7
        BA8           0x00007ba8
        BA9           0x00007ba9
        BAA           0x00007baa
        BAB           0x00007bab
        BAC           0x00007bac
        BAD           0x00007bad
        BAE           0x00007bae

        Radio         0x00007baf
        Print         0x00007bb1

#bb2 - bb4 unused  
        BB2           0x00007bb2
        BB3           0x00007bb3
        BB4           0x00007bb4

        Videos        0x00007bb5
        Pictures      0x00007bb6
        RecTV         0x00007bb7
        Music         0x00007bb8
        TV            0x00007bb9

#bba - bbf unused 
        BBA           0x00007bba
        BBB           0x00007bbb
        BBC           0x00007bbc
        BBD           0x00007bbd
        BBE           0x00007bbe
        BBF           0x00007bbf
#bc1 - bca unused 
        BC1           0x00007bc1
        BC2           0x00007bc2
        BC3           0x00007bc3
        BC4           0x00007bc4
        BC5           0x00007bc5
        BC6           0x00007bc6
        BC7           0x00007bc7
        BC8           0x00007bc8
        BC9           0x00007bc9
        BCA           0x00007bca

        Eject         0x00007bcb
        SlideShow     0x00007bcc
        Visualization 0x00007bcd

#bce - bcf unused 
        BCE           0x00007bce
        BCF           0x00007bcf
#bd1 - bd7 unused 
        BD1           0x00007bd1
        BD2           0x00007bd2
        BD3           0x00007bd3
        BD4           0x00007bd4
        BD5           0x00007bd5
        BD6           0x00007bd6
        BD7           0x00007bd7

        Aspect        0x00007bd8
        Guide         0x00007bd9
        LiveTV        0x00007bda
        DVD           0x00007bdb
#NoGap
        Back          0x00007bdc
        OK            0x00007bdd
        Right         0x00007bde
        Left          0x00007bdf
        Down          0x00007be0
        Up            0x00007be1
#NoGap
        Star          0x00007be2
        Hash          0x00007be3
#NoGap
        Replay        0x00007be4
        Skip          0x00007be5
        Stop          0x00007be6
        Pause         0x00007be7
        Record        0x00007be8
        Play          0x00007be9
        Rewind        0x00007bea
        Forward       0x00007beb
#NoGap
        ChanDown      0x00007bec
        ChanUp        0x00007bed
        VolDown       0x00007bee
        VolUp         0x00007bef
#NoGap
        More          0x00007bf0
        Mute          0x00007bf1
        Home          0x00007bf2
        Power         0x00007bf3
#NoGap
        Enter         0x00007bf4
        Clear         0x00007bf5
#NoGap
        Nine          0x00007bf6
        Eight         0x00007bf7
        Seven         0x00007bf8
        Six           0x00007bf9
        Five          0x00007bfa
        Four          0x00007bfb
        Three         0x00007bfc
        Two           0x00007bfd
        One           0x00007bfe
        Zero          0x00007bff
      end codes

end remote
#
# this config file was automatically generated
# using lirc-0.8.4a(default) on Mon Feb 23 23:55:04 2009
#
# contributed by 
#
# brand:                       Hauppauge
# model no. of remote control: 
# devices being controlled by this remote: PVR-150 Remote (MCE kit)
# SMK dongle 0609:031d
#

begin remote

  name  mceusb_hauppauge
  bits           13
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2674   870
  one           455   427
  zero          455   427
  pre_data_bits   24
  pre_data       0x1BFF82
  gap          106288
  min_repeat      1
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000

      begin codes
          TV                       0x1BB9
          Music                    0x1BB8
          Pictures                 0x1BB6
          Videos                   0x1BB5
          Power                    0x1BF3
          Stop                     0x1BE6
          Record                   0x1BE8
          Pause                    0x1BE7
          Play                     0x1BE9
          Rewind                   0x1BEA
          Foward                   0x1BEB
          Replay                   0x1BE4
          Skip                     0x1BE5
          Back                     0x1BDC
          More                     0x1BF0
          Up                       0x1BE1
          Left                     0x1BDF
          Right                    0x1BDE
          OK                       0x1BDD
          Down                     0x1BE0
          VolUp                    0x1BEF
          VolDown                  0x1BEE
          Home                     0x1BF2
          ChanDown                 0x1BED
          ChanUp                   0x1BEC
          Mute                     0x1BF1
          RecTV                    0x1BB7
          Guide                    0x1BD9
          LiveTV                   0x1BDA
          DVD                      0x1BDB
          One                      0x1BFE
          Two                      0x1BFD
          Three                    0x1BFC
          Four                     0x1BFB
          Five                     0x1BFA
          Six                      0x1BF9
          Seven                    0x1BF8
          Eight                    0x1BF7
          Nine                     0x1BF6
          Star                     0x1BE2
          Zero                     0x1BFF
          Hash                     0x1BE3
          Clear                    0x1BF5
          Enter                    0x1BF4
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.8.4a(default) on Tue Mar 10 19:27:09 2009
#
# contributed by 
#
# brand:  SIIG Vista MCE remote
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  vista_mce
  bits           16
  flags RC6
  eps            30
  aeps          100

  header       2654   889
  one           427   427
  zero          427   427
  pre_data_bits   21
  pre_data       0x37FF0
  gap          69850
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000

      begin codes
          Power                    0xEBF3
          Pictures                 0x6BB6
          Radio                    0xEBAF
          Videos                   0x6BB5
          Music                    0xEBB8
          Rec                      0x6BE8
          Pause                    0xEBE7
          Stop                     0x6BE6
          Skipback                 0xEBE4
          Play                     0x6BE9
          Skipfwd                  0xEBE5
          Rwd                      0x6BEA
          Fwd                      0xEBEB
          Start                    0x6BF2
          Back                     0xEBDC
          More                     0x6BF0
          Volup                    0xEBEF
          Voldown                  0x6BEE
          Chup                     0xEBED
          Chdown                   0x6BEC
          Up                       0xEBE1
          Down                     0x6BE0
          Left                     0xEBDF
          Right                    0x6BDE
          Mute                     0xEBF1
          Rectv                    0x6BB7
          Guide                    0xEBD9
          Livetv                   0x6BDA
          Dvdmenu                  0xEBDB
          1                        0x6BFE
          2                        0xEBFD
          3                        0x6BFC
          4                        0xEBFB
          5                        0x6BFA
          6                        0xEBF9
          7                        0x6BF8
          8                        0xEBF7
          9                        0x6BF6
          *                        0xEBE2
          0                        0x6BFF
          #                        0xEBE3
          Clear                    0x6BF5
          Enter                    0xEBF4
      end codes

end remote


```

Wow... this is crazy.

---

### Post by phroman on 2010-04-01
This is all good, we're almost there, gimmie about an hour an I'll post back.

---

### Post by phroman on 2010-04-01
Soooo..... clooooose.....

In your /etc/lirc/hardware.conf file, change the name in: REMOTE=  to "mceusb", keep it in the quotes.  (i forgot once and it took me an hour to fig it out) 

I didn't see a ~/.lircrc file in the post, but all that does is tell the program lirc to load up the button mapping files for other apps like mplayer, vlc etc.  Its just an include line in the same way as the /etc/lirc/lircd.conf file links to the /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb file.

Next restart lirc at the command line type:  sudo /etc/init.d/lirc restart  This will restart lirc with the changes we've made to the files, and I dare say your remote should be working.  One thing is, how did you load up the Harmony remote with codes from another remote?  You're going to rely on the accuracy of those codes or the file to be correct.  If they're not I'm not sure how to proceed, but let's cross that brige when we come to it.  


If it works, next up: transmitting

EDIT:

One more thing to change in /etc/lirc/hardware.conf  The line:
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
Change the path in quotes to /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb

---

### Post by killabee44 on 2010-04-01
Here is the ~.lircrc:
```

#Custom lircrc generated via mythbuntu-lirc-generator
#All application specific lircrc files are within ~/.lirc
include ~/.lirc/mythtv 
include ~/.lirc/mplayer 
include ~/.lirc/xine 
include ~/.lirc/vlc 
include ~/.lirc/xmame 
include ~/.lirc/xmess 
include ~/.lirc/totem 
include ~/.lirc/elisa 
```

---

### Post by killabee44 on 2010-04-01
I programmed the Harmony to act as the sony-str-da5300es from Harmony's software in windows. It is basically a web interface for programming the Harmony to control your different devices. 

So when I use the Harmony to control Mythtv it will be as if I was using the sony-str-da5300es to do so.

Now in order for this to work, shouldn't we be using the lircd.conf that is set up for the sony-str-da5300es? The one I got from the other forum?

---

### Post by phroman on 2010-04-01
Doh!  Sorry, of course.  Was there a choice for the sony-str-da5300es in the MCC?  If there is that's perfect because that means lirc will have a known working lirc.conf file for this remote.  

The whole problem is that the name filed in /etc/lirc/hardware.conf and /etc/lirc/lircd.conf don't match after selecting a remote in MCC.  Lirc is looking in 2 different files and not finding a matching name, so it won't work.  Aaaand, ~/.lirc/mythtv also has the remote named in it, and of course it must match also.  It's a bug I guess, commented on plenty of times throughout the forums, but its still there.  

So we have 2 options:  If MCC has the sony remote listed, choose it, after you enable it, you will need to check the /etc/lirc/lircd.conf file, check the path to the file it includes,  (That's really your lircd.conf file) probably /usr/share/lirc/remotes/sony/ "whatever it calls the remote".  Remeber this is pointing to a particular file, so the name is important.   See what that file puts in the name field, and edit the 2 fields in /etc/lirc/hardware.conf to match its name and location.

REMOTE="remotename"
REMOTE_LIRCD_CONF=""  to match the path to /usr/share/lirc/remotes/sony/whateveryoucallit file

Then in ~/.lirc/mythtv the remote name must be the same in there too.  

Option 2:
If it MCC doesn't have your remote, I think you have an lircd.conf file, so put it in /usr/share/lirc/remotes/sony/ and you could call it what you want, like lircd.conf.harmony if you wanted to.  Just know it has to be pointed to in your /etc/lirc/hardware.conf and /etc.lirc/lircd.conf files.  Then we'd have to figure out how to create or get a ~/.lirc/mythtv file.  That one takes the button mappings of your lircd.conf file and equates it with the functions of mythtv.

Man I wish I were better at explaining this stuff..   Questions?

---

### Post by killabee44 on 2010-04-03
Ok, in /etc/lirc/hardware.conf what do I put under:

REMOTE_MODULES="lirc_dev lirc_mceusb"

since I see it says *mceusb*.. It just looks like something that needed to be changed.


It looks like the correct path to the new lircd is:

"/usr/share/lirc/remotes/sony/lircd.conf.harmony"



Here is /etc.lirc/lircd.conf:
```

#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/sony/lircd.conf.harmony"

#Configuration for the Microsoft Windows Media Center V2 (usb) : Direct TV Receiver transmitter:
include "/usr/share/lirc/extras/transmitters/directtv/general.conf"
```

Here is ~/.lirc/mythtv
```

# This lircrc file is designed to accompany the sony-str-da5300es
# lircd.conf file, which was designed for the Harmony 880 universal
# remote control.  This should be located in: /.lirc/mythtv

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = Mute
   config = F9
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = VolumeUp
   config = F11
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = VolumeDown
   config = F10
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = ModeDown
# Down Arrow: Decrease time stretch
   config = Shift+F7
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = ModeUp
# Up Arrow: Increase time stretch
   config = Shift+F8
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = PresetPrev
# Channel Down
   config = PgDown
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = PresetNext
# Channel Up
   config = PgUp
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = AmFmToggle
# Prev: Jump to beginning
   config = Ctrl+B
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = DirectionUp
   config = Up
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = DirectionDown
   config = Down
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = DirectionLeft
   config = Left
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = DirectionRight
   config = Right
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = Select
   config = Enter
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = Menu
   config = M
end
  
begin
   remote = sony-str-da5300es
   prog = mythtv
   button = PowerOff
# Exit
   config = Esc
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = OnScreen
# Guide
   config = S
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = Display
# Info
   config = I
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = Dimmer
# Stop
   config = O
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = BalanceLeft
# Skip Back
   config = Home
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = BalanceRight
# Skip Forward
   config = End
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = SndBckDecoding
# Play
   config = P
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = SndFldsMovie
# Record
   config = R
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = TuningDown
# Rewind
   config = <
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = TuningUp
# Fast Forward
   config = >
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = SndFldsMusic
# Pause
   config = Ctrl+P
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = 1
   config = 1
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = 2
   config = 2
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = 3
   config = 3
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = 4
   config = 4
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = 5
   config = 5
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = 6
   config = 6
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = 7
   config = 7
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = 8
   config = 8
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = 9
   config = 9
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = TestTone
# Plus
   config = D
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = 0
   config = 0
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = Equalizer
# E
   config = Ctrl+X
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = AacBilingual
# List
   config = Shift+F1
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = AFD
# MainMenu
   config = Shift+F2
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = AnalogDirect
# LiveTV
   config = Shift+F3
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = AudioSplit
# Zoom
   config = Shift+F4
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = BassBoost
# FullDetails
   config = Shift+F9
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = Input5.1Ch
# Toggle captions
   config = T
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = InputCd
# Program Finder
   config = #
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = EqualizerBassDown
# Slower playback
   config = Shift+F5
end

begin
   remote = sony-str-da5300es
   prog = mythtv
   button = EqualizerBassUp
# Faster playback
   config = Shift+F6
end
```

And here is: /etc/lirc/hardware.conf

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev lirc_mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/sony"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Direct TV Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_mceusb2"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

Oh, I forgot to include the sony lircd file that lircd.conf linked to: at /usr/share/lirc/remotes/sony

```
# located in /usr/share/lirc/remotes/sony
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.3-CVS(default) on Sun Aug 10 22:04:27 2008
#
# contributed by 
#
# brand:                       Sony STR-DA5300ES
# model no. of remote control: Sony RM-AAL008
# devices being controlled by this remote:
#
# This file is specifically designed for the Harmony 880
# universal remote control.  The Harmony 880 must be configured
# to emulate the remote control for a specific device.  The
# Sony STR-DA5300ES receiver was chosen because it has a large
# number of buttons, allowing many additional buttons on the
# Harmony 880 to be configured, for maximum flexibility.
#
# The Harmony configuration for this device also includes some
# additional buttons, such as InputHdmi 1-6, but their codes have a
# different length or something, so they can't be learned without
# using irrecord in raw mode.  Those buttons are not included here.
#
# To help create a corresponding lircrc file, the first set of codes
# has a sample mapping to the standard buttons on the Harmony 880
# remote control.
#

begin remote

  name  sony-str-da5300es
  bits           15
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          256

  header       2477   640
  one          1343   640
  zero          659   640
  gap          46882
  toggle_bit_mask 0x0

      begin codes
# Standard button "Mute".
          Mute                     0x140C

# Standard button "Volume Up".
          VolumeUp                 0x240C

# Standard button "Volume Down".
          VolumeDown               0x640C

# Standard button "Down Arrow".
          ModeDown                 0x7B0D

# Standard button "Up Arrow".
          ModeUp                   0x3B0D

# Standard button "Channel Down".
          PresetPrev               0x440C

# Standard button "Channel Up".
          PresetNext               0x040C

# Standard button "Prev".
          AmFmToggle               0x78B4

# Standard button "Up".
          DirectionUp              0x0F0D

# Standard button "Down".
          DirectionDown            0x4F0D

# Standard button "Left".
          DirectionLeft            0x2F0D

# Standard button "Right".
          DirectionRight           0x6F0D

# Standard button "OK".
          Select                   0x180C

# Standard button "Menu".
          Menu                     0x770D

# Standard button "Exit".
          PowerOff                 0x7A0C

# Standard button "Guide".
          OnScreen                 0x650C

# Standard button "Info".
          Display                  0x690C

# Standard button "Stop".
          Dimmer                   0x590C

# Standard button "Skip Back".
          BalanceLeft              0x320C

# Standard button "Skip Forward".
          BalanceRight             0x720C

# Standard button "Play".
          SndBckDecoding           0x310D

# Standard button "Record".
          SndFldsMovie             0x610D

# Standard button "Rewind".
          TuningDown               0x1A0D

# Standard button "Fast Forward".
          TuningUp                 0x6A0D

# Standard button "Pause".
          SndFldsMusic             0x490D

# Standard button "1".
          1                        0x00B4

# Standard button "2".
          2                        0x40B4

# Standard button "3".
          3                        0x20B4

# Standard button "4".
          4                        0x60B4

# Standard button "5".
          5                        0x10B4

# Standard button "6".
          6                        0x50B4

# Standard button "7".
          7                        0x30B4

# Standard button "8".
          8                        0x70B4

# Standard button "9".
          9                        0x08B4

# Standard button "Plus".
          TestTone                 0x290D

# Standard button "0".
          0                        0x48B4

# Standard button "E".
          Equalizer                0x190D

# Additional buttons.
          AacBilingual             0x740C
          AFD                      0x710D
          AnalogDirect             0x490C
          AudioSplit               0x130D
          BassBoost                0x590D
          DirectTune               0x0A0D
          EqualizerBassDown        0x450D
          EqualizerBassUp          0x050D
          EqualizerTrebleDown      0x750D
          EqualizerTrebleUp        0x350D
          Input5.1Ch               0x270C
          InputAM                  0x2C0C
          InputAux                 0x5C0C
          InputCD                  0x520C
          InputDM                  0x5F0C
          InputDVD                 0x5F0C
          InputFM                  0x0C0C
          InputLink                0x5C0D
          InputLd                  0x6B0C
          InputMd                  0x4B0C
          InputMode                0x060D
          InputPhono               0x020C
          InputSAT                 0x600D
          InputTape                0x620C
          InputTv                  0x2B0C
          InputVideo1              0x220C
          InputVideo2              0x3C0C
          InputVideo3              0x210C
          InputVideo4              0x610C
          InputVideo5              0x410C
          MenuDown                 0x170D
          MenuLeft                 0x270D
          MenuRight                0x670D
          MenuUp                   0x570D
          NightMode                0x020D
          Presets                  0x320D
          PresetShift              0x470D
          Sleep                    0x030C
          Stereo                   0x410D
          SurroundNormal           0x210D

      end codes

end remote
```

I hope these config files help someone looking to do the same thing.

---

### Post by killabee44 on 2010-04-03
Phroman,

It finally works!!

I couldn't have done it without your help. You made it happen and I really appreciate it. Thanks very much. 

Now to tweak some of the buttons that are not doing what they are supposed to do.

---

### Post by phroman on 2010-04-04
Awesome!  :guitar:  

I went through remote control hell trying to get mine set up too, and if it wasn't for people in these forums helping me out, I never would have gotten mine working either.  I'm glad I could finally help someone else out.  I found this link to a good lirc info page:

[http://www.mythtv.org/wiki/LIRC]("http://www.mythtv.org/wiki/LIRC")

I've got some tweaking to do too.   I found a keybindings page, here.

[http://www.mythtv.org/wiki/Keybindings](http://www.mythtv.org/wiki/Keybindings)

  And if you want to get your transmitting going post back also, I think I've fig'd that out.  Again, glad you're up and running!  Seeya

---

