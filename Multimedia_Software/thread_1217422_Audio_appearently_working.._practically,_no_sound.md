---
title: "Audio appearently working.. practically, no sound"
date: 2009-07-19
forum: Multimedia Software
---

### Post by Sifro on 2009-07-19
Hello,

i cannot hear any sound from my freshly installed ubuntu studio.

Here's what i'm experiencing:

1) I open Totem and start playing something: no errors
2) I open the pulseaudio mixer: no errors
3) I go to the playback tab in the mixer and i can see the blue bar moving like when some music is being effectively played (you know, the bar goes left and right and left and right...), but again, no sound at all

The pulseaudio server seems to be working without any problems. My card is supported, with kubuntu it used to work.

What may i do?

edit: forgot to say that the volumes in alsamixer are fine, the speakers are turned on and they are plugged in the computer

---

### Post by igorzwx on 2009-07-19
aplay -l

---

### Post by Sifro on 2009-07-19
scheda 0: NVidia [HDA NVidia], dispositivo 0: AD198x Analog [AD198x Analog]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: NVidia [HDA NVidia], dispositivo 1: AD198x Digital [AD198x Digital]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0

---

### Post by igorzwx on 2009-07-19
man aplay

APLAY(1)                                                              APLAY(1)

NAME
       arecord, aplay - command-line sound recorder and player for ALSA sound&#8208;
       card driver

SYNOPSIS
       arecord [flags] [filename]
       aplay [flags] [filename [filename]] ...

DESCRIPTION
       arecord is a command-line soundfile recorder  for  the  ALSA  soundcard
       driver.  It  supports several file formats and multiple soundcards with
       multiple devices. If recording with interleaved mode samples  the  file
       is automatically split before the 2GB filesize.

       aplay  is  much  the same, only it plays instead of recording. For sup&#8208;
       ported soundfile formats, the sampling rate, bit depth,  and  so  forth
       can be automatically determined from the soundfile header.

       If filename is not specified, the standard output or input is used. The
       aplay utility accepts multiple filenames.

OPTIONS
       -h, --help
              Help: show syntax.

       --version
              Print current version.

       -l, --list-devices
              List all soundcards and digital audio devices

       -L, --list-pcms
              List all PCMs defined

       -D, --device=NAME
              Select PCM by name

---

### Post by igorzwx on 2009-07-19
**[ubuntu_studio] No sound ... :sad:  **
[http://ubuntuforums.org/showthread.php?t=1215803](http://ubuntuforums.org/showthread.php?t=1215803)

---

### Post by igorzwx on 2009-07-19
[IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG] 				**big mistake - gstreamer, alsa, plz help!!!!!** 			

[http://ubuntuforums.org/showthread.php?t=1216484](http://ubuntuforums.org/showthread.php?t=1216484)

---

