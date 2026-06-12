---
title: "Sound suddenly switches off after opening, for instance, Movie Player"
date: 2008-10-15
forum: Multimedia Software
---

### Post by lnajt on 2008-10-15
Sound suddenly switches off after opening, for instance, Movie Player.

I can switch back and forth between embedded audio/video in firefox and opera, but when ever I use any of the following applications my computer suddenly mutes and I have to restart it to get the sound back up:

1. Movie Player
2. Sound Recorder
3. GNU Solfege (this usually does not shut down the sound immediatly)

I have checked alsamixer and my sound preferences - and I have put everything at max volume.

The results of some terminal commands: 


lnajt@lnajt-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lnajt@lnajt-laptop:~$ lspci -v | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

---

### Post by patrickballeux on 2008-10-15
Do you have pulseaudio installed?

I have this problem whenever a software want to use the Alsa driver but this is picked up by PulseAudio instead...

Install "pavucontrol" to see if you see your software connecting to pulseaudio via the Alsa driver (Open Volume Control, 1st tab)...

If it is the case, there are two solutions:

1 - Remove any pulseaudio package to get rid of it, so the real Alsa driver will be use
2 - Run your software using "padsp" which will make them work in pulseaudio correctly. ex: padsp mplayer amovie.avi


Also, make sure that the gstreamer-plugin-pulseaudio is installed.  Totem is probably using the ALSA driver.

On my setup, I selected everything to use pulseaudio (System - Preferences - Sound).  I installed all plusgins for pulseaudio and all tools...

And whenever I have a software that gives me trouble, I start it with padsp...

Good luck!

---

### Post by lnajt on 2008-10-15
Thanks, But I do not have pulse audio installed on my computer.

I think i'll give it a go.

---

