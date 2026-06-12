---
title: "Cannot hear sound through External USB Soundcard Ubuntu 8.10 Intrepid"
date: 2009-02-06
forum: Multimedia Software
---

### Post by rudeboyrg on 2009-02-06
My internal sound card SoundBlaster Xtreme X-fi is not supported by Linux, so I purchased a 6 channel USB audio card. (I'm only interested in stereo sound though) It works perfectly with Windows Vista. But I don't get any sound with Ubuntu.

lsusb output is:
Bus 008 Device 003: ID 0bda:0151 Realtek Semiconductor Corp. Mass Stroage Device
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0ac8:c315 Z-Star Microelectronics Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0d8c:0102 C-Media Electronics, Inc. CM106 Like Sound Device
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I believe the soundcard is C-Media Electronics, CM106

When I go to sound preferences,for sound playback, I select USB Sound Device USB Audio (OSS). (or just OSS). When I hit "test", the power button on my external soundcard starts blinking. It seems like its getting a signal. However, I hear nothing from any of the outputs. I think my mixer volume is up too. But I get no sound. Please help. This is driving me crazy as I've waited weeks to get an external sound card. This is the only thing stopping me from staying with Ubuntu. I have to be able to hear with my computer. With windows, no prob. Ubuntu however isn't working with it.

Thanks for your help in advance.:(

---

### Post by fabietto0102 on 2009-02-16
Same problem here with 8.04. I have an USB dac (a sort of soundcard) which i can only get to work if I use Rhythmbox, but not with Amarok or Exaile, regardless of the Amarok output plugin (alsa, oss, pulseaudio, etc..) or the Exaile playback sink (alsasink, osssink, esdsink) i choose.
My sound preference are set as follows: 
Sound Events: ALSA
Sound playback: USB Audio
Audio Conferencing: both ALSA
Default mixer track: ALSA.

I tried several combinations but, alas, i can't find how to make Amarok playing via the USB dac rather than the pc speakers. 

I found that it's great that ubuntu differentiate music from various sounds, as i really like to hear silly youtube videos and other stuff via the pc speakers but my music via the USB-DAC. For connosseuers, the DAC is the Musical Fidelity V-DAC.

---

### Post by markbuntu on 2009-02-16
The easiest way to get control of a USB device is with pulseaudio


[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by fabietto0102 on 2009-02-18
Thanks Markbuntu! With pulseaudio now I have the settings exactly as I want! Music from Amarok via USB-DAC, all the other sounds via the pc speakers!

There is only one bug, though: Pulseaudio doesn't recognize the audio stream coming from youtube, so I can't use pulseaudio as my default soundcard, but fair enough, I only care that amarok sends the stream to my precious USB-DAC!

---

### Post by xube on 2011-03-14
This works also for **CM106** (C-Media) USB for **Ubuntu 10.04**!

Big Thanks @markbuntu!

---

