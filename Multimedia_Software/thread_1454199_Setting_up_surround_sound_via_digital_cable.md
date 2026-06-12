---
title: "Setting up surround sound via digital cable"
date: 2010-04-14
forum: Multimedia Software
---

### Post by [HUN]Minigun on 2010-04-14
Hi!

I'm using the Ubuntu 10.04 beta 2 64bit system. My mobo is a Gigabyte EP43-DS3L, having a Realtek ALC888 sound chip. It worked fine with 5.1 via 3 analog jack connectors.
However, I got a Panasonic LX600 home theatre system, and I wanna use digital output for this. It works ok, my Xbox 360 via optical cable sounds perfect.
I hooked up my PC with a coax cable, but I can't get the surround working fine. Every speaker works, but when the sound should go to the rear speakers, the front ones play them, just more quietly that the ones sent for them. I tried out that video called "Ac3 Dolby Digital 5.1Ch Sound Test (DivX - Ac3)".
The left, center and right speakers work just fine, but the rears give no sound, I hear the sound for the front speakers. The subwoofer is fully silent.
In the second part, when you should hear the sound from every speaker, everything works, I get sound from all the spakers. When playing stereo MP3s, all the speakers work fine.
In Sound Preferences, the hardware is set to Digital Stereo Duplex (IEC958 ), the output to Internal Audio Digital Stereo (IEC958 ). 

How can I get the rear speakers working when I'm playing some dolby digital-using films?

The test video can be downloaded from here:
[http://www.wooferbasstest.com/download/test-tool-ac3-dolby-digital-5-1ch-sound-test](http://www.wooferbasstest.com/download/test-tool-ac3-dolby-digital-5-1ch-sound-test)

---

### Post by lidex on 2010-04-14
Maybe these will help:
[http://alsa.opensrc.org/DigitalOut]("http://alsa.opensrc.org/DigitalOut")
[http://ubuntuforums.org/showthread.php?t=877811]("http://ubuntuforums.org/showthread.php?t=877811")
[http://ubuntuforums.org/showthread.php?t=1452473]("http://ubuntuforums.org/showthread.php?t=1452473")

---

### Post by mgmeskill on 2010-11-01
I realize this thread is old, but I came across it many times while searching for a solution.  So, I'm posting here in hopes that someone else will benefit from the solution I found.

I have the same Gigabyte mainboard, with said ALC888 on-board sound.  I followed posts, removed pulseaudio, put it back, tried OSS, recompiled bleeding edge alsa packages, set a litany of settings and parms for modules.  I reinstalled Ubuntu a few times after making a mess of the sound config - and after all that I stumbled across this post by oblib;

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10058679](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10058679)

I followed oblib's recipe verbatim on a freshly installed 10.10, and 1 reboot later, I have 5.1 digital audio available under Sound Prefernces -> Hardware.  Tested and working.

Hope oblib's contribution helps another user as much as it helped me.

 -Mike

---

