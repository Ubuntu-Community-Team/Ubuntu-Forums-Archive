---
title: "Gnome Mplayer  Vaapi?"
date: 2011-05-12
forum: Multimedia Software
---

### Post by screaminj3sus on 2011-05-12
I am running natty and I have intel graphics (sandy bridge). I installed Gnome-Mplayer and selected vaapi for output but if I loud up any h.264 video I just get audio only.

This is all gnome-mplayer says when launched from the terminal and I load a video:
```
brandon@brandon-U52F:~$ gnome-mplayer
The volume on 'Default' is 1.000000

** (gnome-mplayer:4073): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `!DBUS_G_PROXY_DESTROYED (proxy)' failed

** (gnome-mplayer:4073): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `!DBUS_G_PROXY_DESTROYED (proxy)' failed
```


My vainfo seems all in order to decode h.264:

```
brandon@brandon-U52F:~$ vainfo
libva: libva version 0.31.1
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/i965_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.31
vainfo: Driver version: i965 Driver 0.1
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
```

Is there a way I can get gnome mplayer working with vaapi?

---

### Post by screaminj3sus on 2011-05-12
I also tried mplayer-vaapi from splitted-desktop but -vo vappi -va vaapi did not work either, and it does not list vaapi at all when I use mplayer -vo help. :/

I can get it to work with vlc, cpu usage goes down but it makes video look choppy which is why I wanted to try mplayer.

---

### Post by screaminj3sus on 2011-05-12
Think I finally found a fix to this in case anyone else is wondering. I edit the config file located in the .mplayer folder in my home folder and added this:

> fs=true
vo=vaapi,xv,
va=vaapi

ao=pulse,

This seemed to work. I am able to play 720p h.264 videos in gnome-mplayer with 5-10% cpu usage.

---

### Post by lakerssuperman on 2011-05-24
Libva, which provides VAAPI, is broken in Natty.  Hopefully it will be fixed soon as this is a show stopper for people trying to use this on lower end hardware or netbooks.

---

### Post by beew on 2011-05-24
> **lakerssuperman said:**
> Libva, which provides VAAPI, is broken in Natty.  Hopefully it will be fixed soon as this is a show stopper for people trying to use this on lower end hardware or netbooks.

Try install Libva from the MOTU ppa and see if that solves the problem. Doubt that the version in Ubuntu's repo will be fixed.

---

### Post by dirkjot on 2011-07-15
It took me a minute or so to find the *right* motu ppa, so here it is:
[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)

It contains daily updated builds of mplayer (if you get tired of daily updates, simply remove the ppa at any point) and of the h.264 decoder.  

This really worked for my aging Athlon 1.2GHz platform with Radeon 9250: I now have full HD video playback at less than 40% CPU load for most avi and m4v files.  Fantastic.

---

### Post by ticket on 2011-07-30
Just tried that motu ppa using natty.
I installed:
 
libx264-115
mencoder
mplayer

There was no libva, but there was a x264 package, which failed to install.

Selecting vaapi in mplayer and playing a movie only played audio.  No video.

Note that if you edit the mplayer config to use:
  vo=vaapi,xv,
then if it fails on vaapi, it uses xv as the fall-back.  

So no joy here.  
Using a ATI radeon HD 4600 with ubuntu built-in driver (8.84 equiv to Catalyst 11.4).

---

