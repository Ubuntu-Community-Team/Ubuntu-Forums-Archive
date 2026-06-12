---
title: "Sound on headphones only..."
date: 2009-05-18
forum: Mythbuntu
---

### Post by JDGlanville on 2009-05-18
Hello All,

I'm a green bean with some sound issues.  The short version of the story: I only get sound playing through my computer's headphone jack.

Here's the long version:

I've started with a clean installation of MythBuntu 9.04.  My computer is connected to my LCD TV through the HDMI cable (there is no other monitor or speakers or sound system connected to the system).  I have upgraded the ALSA drivers to 1.0.20.  Whenever I play anything (it doesn't matter if I Watch TV, Watch Recordings, Watch Videos, Listen to Music or Play DVD), I can only hear things through the headphone jack on the front of my computer.  There is no sound comming from the TV.

I've ensured ALSA is configured properly by using alsaconfig (it's found the "HDA-Inte.    nvidea Corporation MCP78S [GeForc" card/chipset).  I've also ensured that all channels are unmuted through the alsamixer program.

How do I get the sound to be routed to the TV through the HDMI cable?

Configuration information:

[LIST]
[*]Asus M3N78-EM motherboard with HDMI out
[*]MythBuntu 9.04
[*]ALSA 1.0.20
[*]Antec Fusion Remote
[/LIST]

One interesting side piece of information.  If I go into the Asus's BIOS settings, and set the "AZALIA Audio" to "Internal Codec" (the default is "Internal and External Codec"), then I can get audio on the TV, but only when I Watch Videos -- nothing else -- not TV, recordings, DVD or music.  Weird.

So, I know the drivers are working as I'm getting some sound.  How do I route sound to the TV through the HDMI cable?

Thanks

---

### Post by phroman on 2009-05-19
Search for a user on these forums named Dewey_Oxberger and check his posts.  I think he has the same mobo with similar issues.  He got it working if I remember correctly.

---

### Post by JDGlanville on 2009-05-20
Hello again,

I believe I have a solution to my problem.  I'm posting my solution, and environment, in case others can find this information useful, not to mention make it easy for me to re-implement this solution in the future when I have to reinstall!  :-)

The solution primarily came from [DrJohn999's thread about his sound issues with the ASUS M3N78-EM]("http://ubuntuforums.org/showthread.php?t=1140776"), [Dewey_Oxberger's help with another forum user's audio issues]("http://ubuntuforums.org/showthread.php?t=1143028")., plus [Rekoil's instructions on how to upgrade ALSA drivers to 1.0.20]("http://ubuntuforums.org/showthread.php?t=1147977&page=2").

nVidia BIOS:
```
Set "AZALIA Audio" to "Internal + External Codec"
```

Update ALSA drivers to 1.0.20 (see link above).

aplay -l (environment info):
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

aplay -L (environment info):
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Configure /etc/asound.conf:
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
#    Audio output device: ALSA:hdmi_complete    <--- note you have to type in this field
#    Passthrough output devide: Default
#    ... Stereo... ... Passive...
#    Mixer Device: ALSA:default
#    Mixer controls: hdmi_volume                <--- type in this field
# 7) Work your way back to Watch TV and give it a try.

pcm.hdmi_hw {
  type hw
  card 0    #  <-----  Put your card number here
  device 3  #  <-----  Put your device number here
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

```Follow the instructions in the asound.conf file (restart ALSA, set Myth Front End configuration settings, etc).

Run alsamixer:

[LIST]
[*]If there are any channels that are muted (the have a MM in the box at the bottom of the level), unmute them by pressing 'm' when that channel is highlighted.  This includes the IEC958 channels that have no levels above them.  (I think this was my mistake all along.)
[*]Increase every channel to at least 75.
[/LIST]

I believe that that's everything.  If I remember anything else, I'll add it to this thread.

---

