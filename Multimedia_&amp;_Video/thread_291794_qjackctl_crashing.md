---
title: "qjackctl crashing"
date: 2006-11-02
forum: Multimedia &amp; Video
---

### Post by dfro on 2006-11-02
I am trying to set up jack/ardour/qsample/etc for the first time on a new computer.  All I have at the moment is the motherboard's sound card.  I have the Edgy version of Ubuntu.  When I start qjackctl, I get these error messages:

23:41:23.958 Startup script terminated with exit status=256.
23:41:23.958 JACK is starting...
23:41:23.958 jackd -t5000 -dalsa -r44100 -p64 -n2 -D -Chw:0,2 -Phw:0,0
23:41:23.960 JACK was started with PID=17637 (0x44e5).
jackd: unknown driver 'alsa'
23:41:23.968 JACK was stopped with exit status=1.
23:41:24.164 Could not connect to JACK server as client. Please check the messages window for more info.
23:41:26.581 MIDI connection change.

Any ideas on how to fix this?

---

### Post by dfro on 2006-11-03
I tried to recompile jackd and noticed that after './configure', it said:

Build with ALSA support ... false.

For some reason the modified PKG_CONFIG_PATH that I put in my .bash_profile file keeps being dropped. Every time I open a new window I have to ’. ~/.bash_profile’. I wonder how to fix this.

So I tried to rebuild jackd after sourcing .bash_profile and now it says ’Build with ALSA support ... true’.

But, now when I start qjackctl, I get more error messages.

ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
07:14:28.757 Could not connect to JACK server as client. Please check the messages window for more info.
**** alsa_pcm: xrun of at least 2.910 msecs
**** alsa_pcm: xrun of at least 0.175 msecs
**** alsa_pcm: xrun of at least 0.015 msecs
**** alsa_pcm: xrun of at least 1.030 msecs
**** alsa_pcm: xrun of at least 1.415 msecs
07:14:48.677 MIDI connection change.
**** alsa_pcm: xrun of at least 0.092 msecs
07:14:49.084 Could not connect to JACK server as client. Please check the messages window for more info.
**** alsa_pcm: xrun of at least 1.463 msecs
**** alsa_pcm: xrun of at least 4.419 msecs
07:14:51.404 JACK is stopping…

I am trying to recompile qtjackctl and it is not able to find my qt3 libs:

checking whether QTDIR environment variable is set... /usr/include/qt4:/usr/share/qt4:/usr/include/qt3:/usr/share/qt3
checking for main in -lqt-mt... yes
checking for Qt library version >= 3.1.1... no; Qt 3.1.1 or greater is required


You can see from the output that my setting in .bash_profile has been read.  Am I doing this wrong?  How do I check to see which version of qt3 I have?
A tutorial on how to get all of the environment variables set up for the dev libraries - gtk+, qt - so that the various audio apps compile would be great, if it has not already been done.  Also, a summary on how to reset the various config files, too.  I am very new to all of this stuff.

---

### Post by dfro on 2006-11-13
I went through the UbuntuStudioPreparation steps first thing after installing ubuntu edgy.  I have read about the ubuntumusique-repo kernel patch, but I have a Pentium D 930 Dual-core Processor.  I recall the tutorial saying it will not work on dual core processors.  Is this correct?  Any ideas on how I can get up and running with jackd, qtjackctrl?

---

### Post by nalmeth on 2006-11-13
Does qjackctl work now in Edgy? Or have you been using Edgy all along and the situation is still the same?

---

### Post by dfro on 2006-11-13
> Does qjackctl work now in Edgy? Or have you been using Edgy all along and the situation is still the same?

I first installed Edgy and went through the UbuntuStudio Preparations tutorial before trying to get jack, qjackctl, ardour, etc working.

My current status with jack, qjackctl is as follows.  If I run 'jackd' from the command line, I get:
> 
$ jackd -d alsa
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback

It looks like jack is working.  But when I next run 'qjackctl' from the command line, I get:

> $ qjackctl
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Warning: no locale found: /usr/share/locale/qjackctl_en_US.UTF-8.qm

Also, the GUI window launches and displays this message:

> jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
`default' server already active
14:01:59.752 JACK was stopped with exit status=1.
14:01:59.945 Could not connect to JACK server as client. Please check the messages window for more info.
14:02:05.182 MIDI connection change.

qjackctl cannot connect to jack server as client. (?)

Thanks for the help.

---

### Post by nalmeth on 2006-11-13
Just run qjackctl first, and hit start to launch jackd. I think the problem arises from when you're *first* launching jackd manually, *then* launching qjackctl.

---

