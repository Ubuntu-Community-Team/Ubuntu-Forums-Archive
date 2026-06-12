---
title: "HDMI volume control, editing asound.conf"
date: 2010-03-24
forum: Multimedia Software
---

### Post by paulrogers on 2010-03-24
Hi there,

Ive finally got my sound working, but the volume control wont change the sound and I have to use my TV's remote control. 

As instructed I did:
```
paul@paul-desktop:~$ aplay -L
front:CARD=SB,DEV=0
    HDA ATI SB, VT1708B Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, VT1708B Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, VT1708B Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, VT1708B Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, VT1708B Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, VT1708B Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, VT1708B Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
hdmi:CARD=HDMI
    HDA ATI HDMI, ATI HDMI
    HDMI Audio Output

```

I have deweys.asound.conf to edit:
```
# Jon B's ASound.Conf file for HDMI Audio on MythTV
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
#    sudo cp deweys_asound.conf.txt /etc/asound.conf
#      or 
#    sudo cp deweys_asound.conf.txt $HOME/.asound.conf
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
```

Im wondering if somebody could help me with this so I can start controlling the sound via the controls on my keyboard, which do control normal sound on ubuntu.

Thanks,
Paul

---

### Post by paulrogers on 2010-03-25
Is nobody able to help me with this?

---

### Post by guikubivan on 2010-08-08
I used a slightly different .asoundrc config from: [http://ubuntuforums.org/showthread.php?t=1501027](http://ubuntuforums.org/showthread.php?t=1501027)

However, I had to comment out the sampling rate line. Then I could see a volume slider on alsamixer called hdmi_vol (far right for me).
```
#    rate 48000
```

---

