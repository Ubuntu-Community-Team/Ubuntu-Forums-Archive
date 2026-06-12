---
title: "ALSA, intel-hda-audio set up"
date: 2009-01-26
forum: Multimedia Software
---

### Post by konradpiskorz on 2009-01-26
Problem:
1 - No mixers work for the soundcard
2 - initial volume too low

Trying to get alsamixer to run from the terminal only results in alsamixer: function snd_mixer_load failed: No such file or directory.

I cannot find any relevant documentation on this except for benign problems like permissions.

Gnome's mixer has a large collection of options and volume sliders, all of which have no effect at all.

ALSA needs some tweaking.  Clearly, I need to do something to get sound working properly, I just have no idea where to start and can't find any information...

My soundcard is an Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) which usues the snd-hda-intel drivers for alsa.

I have no idea what the sound architechture is in ubuntu or linux.  Would I want to reinstall alsa and sound drivers?  If so, how?  Will I need to compile from source as the ubuntu repo's aren't working?  Could there be modules I need to load into the kernel?  It seems that alsaconf is the general solution used in the past for this but has been removed due to bugs in alsa-utils.  Could I just snag on old version?  Will it break everything?

Konrad

---

### Post by Linuxdork on 2009-01-26
Couple of questions to get started.  Which version of Ubuntu are you using?  Is this a fresh install or an upgrade?  Is the snd-hda-intel module loaded (sorry if this is a stupid question, I just want to make sure)?

---

### Post by konradpiskorz on 2009-01-26
1) Using version -> Ubuntu 8.04 Hardy

2) Upgraded from an 7.04 Feisty install

3) snd_hda_intel is loaded according to lsmod.  Im assuming the fact that the module is snd_hda_intel and alsa uses snd-hda-intel isnt an issue.

Also, sound works, albeit too quietly to actually be listenable.  It's just I have to access to my soundcards mixers to bring it up.

And just in case, results of uname -a
Linux konrad-laptop 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux

---

### Post by Linuxdork on 2009-01-26
This may be due to pulseaudio which is the new soundserver in hardy.  It wasn't configured very well and so a lot of people have problems with it.  I recommend following this howto: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

It fixed all the issues I was having and I have seen it fix others.  As you said the module snd_hda_intel is loaded so it most likely isn't an issue with the kernel recognizing it.  Keep us posted.

---

### Post by konradpiskorz on 2009-01-26
Well that was it :)

I followed the how-to step by step and my sound is no longer buggered :)

Thanks a lot Linuxdork!

Konrad :)

---

### Post by Linuxdork on 2009-01-27
No problem. I'm glad I could help.

---

