---
title: "XBMC and nVidia drivers: What to do about video tearing?"
date: 2010-02-16
forum: Multimedia Software
---

### Post by charlie. on 2010-02-16
I have finally acquired Internet to my house and, since I again have access to the Intarweb and fabulous forums such as these, I felt that it was time to put Linux back on my home PC for all but gaming. Quickly, Ubuntu 9.10 x64 came down the line and a little while later, I have a fully installed Ubuntu system. On top of the vanilla install, I've added the nVidia proprietary drivers (using the U.I. to install them for the first time ever... and being much surprised by the fact that that WORKED!)

Now I have some hardware:
Intel E6850 Core 2 Duo
nVidia GeForce GTX 275
Some (4GB) generic RAM
Lots (all added up, over 1 TB) of hard-drives.
Onboard sounds (Intel HD Audio)

And some Software:
Ubuntu 9.10 Karmic, x86_64.
nVidia Proprietary Drivers
LIRC (for my Windows Media Centre (green button) remote)
XBMC (off the PPA)

... and all is well.

But all is NOT well. Despite the fact that I've achieved this without hacking a SINGLE LINE OF CONFIG FILES or compiling a single program from source, I do have a problem: I have some serious video tearing in XBMC when playing video.

I have enabled "Vertical blank sync" under System -> System -> Video (inside XBMC) but this hasn't changed anything. (It HAS given XBMC a tendency to hang, however.)

Specifically, I noticed this when watching h.264 video from a Matroska container.

How should I start tackling this problem? I've fallen in love with XBMC already (out-the-box support for my remote and such a customisable U.I.) and don't want to lose it to some silly tearing problem.

---

### Post by mutex023 on 2010-02-16
If you are running compiz then you might want to check this - [http://tombuntu.com/index.php/2009/09/20/make-compiz-run-smoothly-and-without-tearing/](http://tombuntu.com/index.php/2009/09/20/make-compiz-run-smoothly-and-without-tearing/)

---

### Post by aeiah on 2010-02-16
have you enabled syncing in nvidia-settings?

[img]http://img109.imageshack.us/img109/4561/screenshotnvidiaxserver.png[/img]

i have a script which fires up xbmc under a different x session (basically so it turns off my main monitor, and puts it on my hdtv, which is usually off during normal computer use). mine is synced perfectly. the script that does it makes sure nvidia-settings is set correctly by setting these flags just before starting xbmc:

```

nvidia-settings -a :1.0/SyncToVBlank=1 &
nvidia-settings -a :1.0/AllowFlipping=1 &
nvidia-settings -a :1.0/XVideoTextureSyncToVBlank=1 &
nvidia-settings -a :1.0/XVideoBlitterSyncToVBlank=0

```

however, since you're using the same screen you should be able to permanently set them within the nvidia-settings gui and not bother with scripts or command lines.

---

### Post by aeiah on 2010-02-16
ps: you shouldnt be getting skipping with the sync options enabled in xbmc (obviously). you should also be able to activate VDPAU in xbmc when you've got the tearing issue sorted, to enjoy 1080p HD content with hardly any CPU overhead thanks to your graphics card :cool:

---

### Post by sailor420 on 2010-06-12
> **mutex023 said:**
> If you are running compiz then you might want to check this - [http://tombuntu.com/index.php/2009/09/20/make-compiz-run-smoothly-and-without-tearing/](http://tombuntu.com/index.php/2009/09/20/make-compiz-run-smoothly-and-without-tearing/)

This seems to have fixed my very similar issues! Thanks!

---

### Post by anotherdike on 2011-02-14
> **mutex023 said:**
> If you are running compiz then you might want to check this - [http://tombuntu.com/index.php/2009/09/20/make-compiz-run-smoothly-and-without-tearing/](http://tombuntu.com/index.php/2009/09/20/make-compiz-run-smoothly-and-without-tearing/)

This seems to have worked for me, too.  I am running 10.10 x86 with a GForce 9400 series card using the proprietary nvidia drivers.  I had experienced tearing when using both Boxee and XBMC.  

Thanks for the tip!

---

### Post by buster2209 on 2011-02-14
Take a look at the following thread;

[http://ubuntuforums.org/showthread.php?t=1687207](http://ubuntuforums.org/showthread.php?t=1687207)

I have Revo 3700 I use with XBMC and have tear free NVidia with compiz effects *enabled*.

---

