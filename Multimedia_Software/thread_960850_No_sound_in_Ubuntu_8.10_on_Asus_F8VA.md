---
title: "No sound in Ubuntu 8.10 on Asus F8VA"
date: 2008-10-27
forum: Multimedia Software
---

### Post by Big_Goose on 2008-10-27
Hey guys, I'm not really sure how to fix this.  I hope someone can help.

I just installed Intrepid on my Asus F8VA laptop and everything is working perfectly but I just cant seem to get the sound working.  However, ubuntu seems to recognize both the sound card and the digital output of the hdmi port.

lspci -nn | grep Audio
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
01:00.1 Audio device [0403]: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series] [1002:aa20]

Under System>Sound>Preferences I have numerous options to select from.
HDA Intel ALC662 Analog (ALSA)
HDA Intel ALC662 Digital (ALSA)
HDA Intel HDMI ATI HDMI (ALSA)
HDA Intel ALC662 Analog (OSS)
HDA Intel ALC662 Analog (OSS)
HDA Intel ALC662 Analog (OSS)
ALSA - Advanced Sound Linux Architecture
OSS - Open Source Sound
PulseAudio Sound Server

I have no idea which one to select but I've tried them all.  But, when I tried to test the HDA Intel ALC662 Analog (ALSA) entry I get this error message.

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

If anyone could give me some suggestions, I would appreciate it.  Thanks.

---

### Post by freqmode on 2008-11-04
How did you get the video working!!

---

