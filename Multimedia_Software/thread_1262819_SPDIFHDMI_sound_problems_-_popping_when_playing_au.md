---
title: "SPDIF/HDMI sound problems - popping when playing audio"
date: 2009-09-10
forum: Multimedia Software
---

### Post by frigginacky on 2009-09-10
I recently upgraded to a new video card that can handle audio over HDMI using a cable from the SPDIF header on the motherboard to the card.  I got sound working by:

1. Upgrading to ALSA 1.0.20 using the script here: [http://ubuntuforums.org/showthread.php?t=1046137]("http://ubuntuforums.org/showthread.php?t=1046137").
2. Changing the default device from the onboard HDMI to digital in my asound.conf.

This works great...except there's a loud popping/crackling whenever I start or stop audio.  It occurs for all file formats in every player I've tried: VLC, MPlayer, Xine, Mythtv, Exaile, etc.  The sound quality is fine during playback; it's only at the beginning and end that I get the noise.

Possibly relevant info:
OS: Mythbuntu 9.04 64-bit w/ Ubuntu desktop installed
Mobo: ASUS M3N78-VM [(newegg link)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131318")
New vid card: PNY XLR8 GeForce 9800 GT [(newegg link)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814133279")

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
(Device 3 in the onboard HDMI, device 1 is what I'm using)

My asound.conf, snagged from the second post here: [http://ubuntuforums.org/showthread.php?t=1143028]("http://ubuntuforums.org/showthread.php?t=1143028"). This had onboard HDMI audio working like a charm before the new card.  All I changed was the device number.
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
  device 1   #  <-----  Put your device number here
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

Anyone know the cause of or solution to this problem?  This box is an HTPC, so an audio issue as annoying as this one just ain't gonna fly.  Any help will be deeply appreciated!

---

### Post by frigginacky on 2009-09-11
Nobody?  This is driving me crazy!

---

### Post by frigginacky on 2009-09-18
In case anyone has the same problem and happens across this thread, I finally solved this by installing PulseAudio 0.9.15.

---

### Post by jwssr on 2009-09-18
here is great link about pulse audio..which I think may be required reading..was a greatt help to me.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

also..I to use hdmi sound..  I have ati3200 video onboard with 2 digital sinks and 1 analog sink.  plus I have a bluetooth headset.  I can have 4 different audio apps and outpiuuting sound to each output..simultaneously..

I have found that these 3 apps are required on my karmic box

paman   
pavucontrol
gnome alsamixer
and the sound app in system/preferences/sound

ice958 has to checked to provide digital sound.

good luck.

---

