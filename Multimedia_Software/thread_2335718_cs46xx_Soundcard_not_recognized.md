---
title: "cs46xx Soundcard not recognized"
date: 2016-08-31
forum: Multimedia Software
---

### Post by furant2 on 2016-08-31
I've tried to follow multiple similar posts to no avail.  I've tried purging and re-installing alsa and pulseaudio, manually loading the cs46xx module.  I'm not new to 'nix and usually I can search and follow similar issues to work through problems, but nothing I've tried has worked here.  I tried to follow the instructions here for the Turtle Beach Santa Cruz:
[http://www.alsa-project.org/main/index.php/Matrix:Module-cs46xx](http://www.alsa-project.org/main/index.php/Matrix:Module-cs46xx)
but had issues with "modprobe snd-seq-oss" and when I try to run alsamixer, I receive:
```
cannot open mixer: No such file or directory
```
lspci | grep "Audio"
```
03:06.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
```
cat /proc/asound/cards
```
--- no soundcards ---
```
alsa-info.sh provides
[http://www.alsa-project.org/db/?f=021d01bab07de84de8af88fdcfbc8b34cfa53444](http://www.alsa-project.org/db/?f=021d01bab07de84de8af88fdcfbc8b34cfa53444)

Any help is appreciated.

---

### Post by furant2 on 2016-08-31
I went back through the compilation and installation of the drivers, firmware and utils.  I had to track down a couple of issues (like the kernel version.h not being found, curses library not being installed), then I added my main user to the audio group and it worked.

Hopefully this can be helpful for someone else.

---

### Post by Yellow Pasque on 2016-09-01
The ALSA page you link to is outdated (alsa-driver was moved into the kernel tree years ago). Your alsa info shows the problem is the firmware:
```
[   27.113659] snd_cs46xx 0000:03:06.0: Direct firmware load for cs46xx/cwc4630 failed with error -2
[   27.113669] snd_cs46xx 0000:03:06.0: firmware load error [cwc4630]
```

One should only need to obtain the firmware (not included in Ubuntu's alsa-firmware for legal reasons) to get this card working on a modern version of Ubuntu.
[https://ubuntuforums.org/showthread.php?t=2260339](https://ubuntuforums.org/showthread.php?t=2260339)

---

