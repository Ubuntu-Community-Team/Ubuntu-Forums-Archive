---
title: "Silent Feisty, driver install problems"
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by GFC2 on 2007-07-04
No sound at all, not streaming, not CD, nada.  The problem is confined to audio.  Video playback is OK but silent.  Audio files register and playback timers count, so the it's not an applications problem.  Alsa mixer is not muted.  Kernel is 2.6.20-16 with soundcore module verified.

aplay -l yields: card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
lspci -v yields: 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 

Found drivers for the Intel ICH southbridge HD-audio and modem, ICH7 chipset on the ALSA website.  Downloaded the 1.0.14 driver, library, and utilities files, and proceeded per the instructions for that driver on the ALSA website:

cd /usr/src
mkdir alsa
 cd alsa
cp /downloads/alsa-* .
bunzip2 alsa-driver-1.0.14.tar.bz2
tar -xf alsa-driver-1.0.14.tar.bz2 

With a little finagling (desktop filepath substituted for the downloads source file and a couple of sudo's added to commands) I was able to successfully execute this far.  The next command has me stopped cold.  

cd alsa-driver-1.0.14.tar.bz2  yields:  

bash: cd: alsa-driver-1.0.14.tar.bz2: Not a directory

Can't get around this one.      No install, no sound, and one frustrated noob. Help!

---

### Post by AlteredAgain on 2007-07-05
yeah i have the same exact problem.

what's the trouble with Intel sound cards on Ubuntu??

are they even compatible?

---

### Post by GFC2 on 2007-07-05
AlteredAgain,

Is your exact same problem just the lack of sound or failure to install drivers?  There is no guarantee of gaining audio with updated drivers, but everything else I know about checks out like it should work.  The current drivers are 1.0.14rc1 - four behind the current generation.

If you find a solution, drivers or otherwise, I'd love to hear about it!

---

