---
title: "Is ATI HDMI driver limited to stereo only?"
date: 2012-01-01
forum: Multimedia Software
---

### Post by PeterTaps on 2012-01-01
Folks,

My setup:

ASUS F1A75V-PRO Motherboard + AMD A6 CPU. The motherboard has integrated HDMI out port.

The box is connected to Pioneer AV receiver that in turn is connected to an overhead projector.

When I install Windows 7 on the box and apply all the drivers, the 5.1 setup works perfectly. My testing of each individual speakers work fine.

However, for the past three days, I have been struggling with getting my the audio to work under Ubuntu.

Ubuntu 11.10 install just displays blank screen. All the suggestions (nomodeset, etc.) did not work.

Ubuntu 11.04 installs but cannot get ATI FGLRX driver to install. A number of errors. Without this driver, it appears I cannot get speakers to work at all.

Today, I tried 12.04 daily build. It installed fine. Even FGLRX driver installed properly.

However, under sound preferences, I only see "HDMI Digital Stereo Output" as an option. There is no HDMI 5.1 option.

When I run "speaker-test -c 6," I can hear front left, center, and front right speakers only. There is not sound from the other speakers.

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ aplay -L
 aplay -L
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, HDMI 0
    HDMI Audio Output
....

I have tried many setting from posts on various forums but nothing seems to work. 

I even added the following line to /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel model=3stack-6ch-dig

However, it seems this option is meaningful only for intel/nvidea and not amd/ati.

I would appreciate it if someone can tell me if ATI HDMI is limited to just the front speakers or is there something that I am missing?

 Thank you in advance for your help.

Regards,
Peter

---

### Post by wild_oscar on 2012-05-19
Did you ever solve this issue?

---

### Post by Lisiano on 2012-05-19
@wild_oscar install [Pavucontrol](apt://pavucontrol), open it via Alt+F2 or a terminal (Ctrl+Alt+T) or from Dash, then go to Configuration and switch HDMI to 5.1 . Might work.

---

### Post by config.sys on 2012-05-21
I am having the same exact problem. 

I was going to try this:

[http://www.momentaryfascinations.com/technology/getting.7.1.hdmi.audio.working.under.ubuntu.html](http://www.momentaryfascinations.com/technology/getting.7.1.hdmi.audio.working.under.ubuntu.html)

but I don't have a Hardware tab under Sound Devices. Grrr!

---

