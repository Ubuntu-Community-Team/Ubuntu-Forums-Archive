---
title: "FFmpeg missing dependencies"
date: 2009-12-14
forum: Multimedia Software
---

### Post by bigwoof on 2009-12-14
Hi there,

I was trying to install ffmpeg and got the following error when I typed:

```
sudo apt-get install ffmpeg
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ffmpeg: Depends: libavcodec52 (< 4:0.5+svn20090706-99) but it is not going to be installed or
                   libavcodec-extra-52 (< 4:0.5+svn20090706-99) but 4:0.5+svn20090926-0ubuntu3~tj~ppa1k is to be installed
          Depends: libavdevice52 (< 4:0.5+svn20090706-99) but it is not going to be installed or
                   libavdevice-extra-52 (< 4:0.5+svn20090706-99) but 4:0.5+svn20090926-0ubuntu3~tj~ppa1k is to be installed
          Depends: libavfilter0 (< 4:0.5+svn20090706-99) but it is not going to be installed or
                   libavfilter-extra-0 (< 4:0.5+svn20090706-99) but 4:0.5+svn20090926-0ubuntu3~tj~ppa1k is to be installed
          Depends: libavformat52 (< 4:0.5+svn20090706-99) but it is not going to be installed or
                   libavformat-extra-52 (< 4:0.5+svn20090706-99) but 4:0.5+svn20090926-0ubuntu3~tj~ppa1k is to be installed
          Depends: libswscale0 (< 4:0.5+svn20090706-99) but it is not going to be installed or
                   libswscale-extra-0 (< 4:0.5+svn20090706-99) but 4:0.5+svn20090926-0ubuntu3~tj~ppa1k is to be installed
E: Broken packages
```


Pleas Help

---

### Post by mc4man on 2009-12-14
Pretty simple - you've used a ppa, tj~ppa1k, to installed shared ffmpeg libs ( libavcodec, libavformat, ect.
If you want ffmpeg (shared .deb package), then you'll need to get the ppa's ffmpeg. (if available

One of these (jaunty or karmic..?
[https://launchpad.net/~intuitivenipple/+ppa-packages](https://launchpad.net/~intuitivenipple/+ppa-packages)

Otherwise remove the current libs, run an update, and install the ubuntu repo's packages.
Or

[Build]("http://ubuntuforums.org/showthread.php?t=786095") your own static ffmpeg

Using  non repo shared ffmpeg libs is possible and while I always replace default ubuntu shared ffmpeg libs **once**, you need to  make sure you don't break current depends. Or at least not ones that matter to you..

A static build of ffmpeg itself is far better than using the repo's or ppa's ffmpeg. referring to ffmpeg itself, not the shared libs

---

### Post by bigwoof on 2009-12-14
Hi mc4man,

Thanks for the Quick response, I removed the packages in question (it looks like it also removed VLC) and then I managed to install ffmpeg (and VLC) with no problems.

Thanks for the Help

---

