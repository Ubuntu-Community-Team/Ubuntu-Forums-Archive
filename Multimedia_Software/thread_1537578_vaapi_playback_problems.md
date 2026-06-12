---
title: "vaapi playback problems"
date: 2010-07-23
forum: Multimedia Software
---

### Post by ihavoc on 2010-07-23
Hi all, I get corruption on playback when trying to use vaapi, whether it be mplayer-vaapi or xbmc. See image below.
This is 10.04 64 bit using an ati 5770 video card have tried 10.3 10.4 and 10.6 fglrx drivers.
I have also got libva1_0.31.1-1+sds4_amd64.deb, libva-dev_0.31.1-1+sds4_amd64.deb and xvba-video_0.7.2-1_amd64.deb installed.
 

[IMG]http://img59.imageshack.us/img59/2075/test1k.png[/IMG]

here is my vainfo

```
vainfo 
libva: libva version 0.31.1-sds1
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.31
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA API - 0.7.2
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointIDCT
      VAProfileMPEG2Main              :	VAEntrypointIDCT
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

```

any help would be appreciated 
Thanks 
Greg

---

### Post by ihavoc on 2010-07-24
well just found out on another forum that this normal output with the ati hd5xxx series and may not be resolved for some time.
so much for being cutting edge:(

---

### Post by csaratchand on 2010-07-24
Try the mplayer-vaapi package from: 
[https://launchpad.net/~falk-t-j/+archive/lucid](https://launchpad.net/~falk-t-j/+archive/lucid)
i.e. add the PPA and install its mplayer-vaapi package.

---

### Post by MetaDark on 2010-09-02
When I add that repository I still can't find and install mplayer-vaapi

I am trying;

```
sudo apt-get install mplayer-vaapi
```

But I get the error;

```
E: Couldn't find package mplayer-vaapi
```

Do I have to do it some other way?

---

### Post by tripmix on 2010-09-02
Here is a usefull apt command that might help you find the exact package name if it's inn there.```
apt-cache search mplayer
apt-cache search vaapi
apt-cache search mplayer vaapi
``` you get the picture and don't forget to run apt-get update after adding a repo, I've done that :D

---

