---
title: "Mounting .ISO Files as Discs"
date: 2012-04-01
forum: Multimedia Software
---

### Post by GraceLinux on 2012-04-01
I've made disc images of my DVDs and Blu-rays and saved them to my HDD.  In Windows I just double click and it mounts the .iso as as if it were a normal DVD/Blu-ray.  I use Slysoft's Virtual Clone Drive in Windows to do this.  Is there any similar for Ubuntu?  

Also does Ubuntu support Blu-ray playback? My Blu-ray .iso files are free from copy protection I'm not sure if this matters though.

Thanks for your help. :popcorn:

---

### Post by qyot27 on 2012-04-01
[CDemu](http://en.wikipedia.org/wiki/CDemu)

I can't remember if it's in the repositories, though.  There is a PPA for it.

Blu-ray playback is dependent on the media player.  VLC and mplayer should both support it.

---

### Post by GraceLinux on 2012-04-01
Thanks Qyot27 I haven't been using Linux that long I don't know what a PPA is. #-o

I didn't know VLC supported Blu-ray playback!  Is this exclusive to the Linux version? I have to use PowerDVD 10 on Windows and it's a real pain. :lolflag:

Thanks again,

Grace ):P

---

### Post by halibaitor on 2012-04-01
You might try AcetoneISO.  It may be useful to you.

---

### Post by qyot27 on 2012-04-02
> **GraceLinux said:**
> Thanks Qyot27 I haven't been using Linux that long I don't know what a PPA is. #-o
Personal Package Archive.  Basically an unofficial repository maintained by an individual user.  Unofficial by the main distro, anyway - sometimes the ones maintaining the PPAs are the original authors of the software, so it wouldn't quite be 'unofficial' to their point of view.

Found the link:
[https://launchpad.net/~cdemu/+archive/ppa](https://launchpad.net/~cdemu/+archive/ppa)



It is also possible to mount ISO files in Linux using the loop device, and that doesn't take any additional software (although it likely has to be done via the Terminal, not the GUI).  My suggestion for CDemu is that it covers other disc image formats as well, and it also supplies an indicator applet or whatever for mounting images through the GUI.


> I didn't know VLC supported Blu-ray playback!  Is this exclusive to the Linux version?
It might be a very new feature that isn't yet in the standard builds (i.e., you might have to either compile VLC from source or grab a nightly build), but it should be true of all the OSes that VLC supports: Windows, Linux, Mac, etc.  It can only play unencrypted disc structures, though (at least, without further meddling that I'm not entirely sure about).

This is because - to my knowledge - the support is actually due to libbluray, so anything that can link to libbluray should be able to do it.

---

