---
title: "Static with VLC in Feisty"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by Dr. Faustus on 2007-05-01
I keep getting static on my audio files in Feisty.  What do you think is the cause of this?   A codec?  Should I report the bug? 

It was fine before the upgrade.

---

### Post by jcarlock on 2007-05-03
I have the exact same problem with vlc.  I tried apt-get remove vlc vlc-nox.  also deleted ~/.vlc and usr/share/vlc.  I then reinstall vlc, but the issue remains.

I am going to try and build it myself.  It worked fine for me for a while but then I rebooted one day and its all F***ed.  MPlayer runs fine with the exact same audio files.  The only thing I changed today was installing cedega and attempted to run CSS through steam.

Who know what causes this.  I would definitely submit a bug report for this.  I have an Intel HDA .... alsa driver, etc.

JC

---

### Post by jcarlock on 2007-05-03
A bug report was already submitted.  On the first page of google if you search feisty static audio.  The second of two bug reports.

JC

---

### Post by jcarlock on 2007-05-03
SOLUTION!!!!!!!

Run apt-get remove vlc vlc-nox

Then it will tell you about the lib's it does not need.  Copy them and paste them at the end of apt-get remove.

i.e.

sudo apt-get remove libdc1394-13 libwxgtk2.6-0 libpostproc0d libdvbpsi4 libavformat0d libxosd2
  libvlc0 libwxbase2.6-0 libgsm1 libdvdnav4 libiso9660-4 libkadm55
  libavcodec0d libmodplug0c2 libtar libvcdinfo0 libmpcdec3 libsdl-image1.2

Then I ran 'sudo apt-get install vlc'

Problem resolved.

---

### Post by jcarlock on 2007-05-04
I lied.  It helped at first, but now it returned.  I am just going to use mplayer until Gibbon is out.

JC

---

### Post by hotani on 2007-05-05
Same problem here. Audio in some files are filled with static when playing in VLC. In Totem, the same file is fine.

---

