---
title: "problem with playing mp3 in ubuntu 9.04"
date: 2009-05-25
forum: Multimedia Software
---

### Post by Hossein309 on 2009-05-25
Hi,
Recently i upgrade ubuntu 8.04 to ubuntu 9.04 and have problem with playing mp3 in this ver.
When i try play mp3 file, player program search for some plug in and says that: can't find MPEG-1 layer (3) decoder.

Anyone can help me .

Thanks.

---

### Post by barisurum on 2009-05-25
Try to install [COLOR="Red"]ubuntu-restricted-extras[/COLOR] in synaptic package manager. This should make every codec work.

---

### Post by navneeth on 2009-05-25
> **barisurum said:**
> Try to install [COLOR="Red"]ubuntu-restricted-extras[/COLOR] in synaptic package manager. This should make every codec work.

Can I avoid installing certain packages like MS Fonts, cabinet file extractors and unrar? 

```
navneeth@ubuntu:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for navneeth: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cabextract libavcodec-unstripped-52 libavutil-unstripped-49 ttf-liberation
  ttf-mscorefonts-installer unrar
The following packages will be REMOVED
  libavcodec52 libavutil49
The following NEW packages will be installed
  cabextract libavcodec-unstripped-52 libavutil-unstripped-49 ttf-liberation
  ttf-mscorefonts-installer **ubuntu-restricted-extras** unrar
0 upgraded, 7 newly installed, 2 to remove and 0 not upgraded.
Need to get 5183kB of archives.
After this operation, 2470kB of additional disk space will be used.
Do you want to continue [Y/n]? n

```

---

### Post by navneeth on 2009-05-25
I'm having the similar/same? problem as Hossein309 does. All the bad and ugly stuff have been installed, and I just now installed libavcodec-unstripped-52 and libavutil-unstripped-49. Even after a reboot, when I open an mp3 file using Totem, it says that a MPEG-1 Layer 3 decoder is required and that it is not installed.

---

### Post by Hossein309 on 2009-05-25
In ubuntu 8.04, i hasn't this problem without installing ubuntu-restricted-extras :(

---

### Post by barisurum on 2009-05-25
> In ubuntu 8.04, i hasn't this problem without installing ubuntu-restricted-extras

I solved my codec problem with installing restricted extras, but just installing gstreamer0.10-plugins should do the job too.

---

### Post by Hossein309 on 2009-05-26
> **barisurum said:**
> I solved my codec problem with installing restricted extras, but just installing gstreamer0.10-plugins should do the job too.

Yes it is ture gstreamer is enough.

GStreamer extra plugins for mp3, sid, mpeg1, mpeg2, Ac-3,
GStreamer ffmpeg video plugin for mpeg, divx, mpeg 4, ac3, wma

Thank you.

---

