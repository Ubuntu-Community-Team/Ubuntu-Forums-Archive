---
title: "Up to date FFmpeg xvid and x264 builds ppa"
date: 2009-03-02
forum: Multimedia Software
---

### Post by HolyDuck on 2009-03-02
Seeing as how the ubuntu reps are full of horribly outdated, 
and/or "broken" media packages. 
and me spending alot of time doing ffmpeg,mplayer and x264 support

i decided to try and do something to fix the situation as a debian user:P

currently i just have ffmpeg with up to date faac,x264,xvidcore,amrwb and amrnb
and its built with the annoying debian/ubuntu guideline of everything compiled as shared :P

its also currently based on debian-multimedia, though i eventually plan to make scripts for getting svns for ffmpeg,x264,mplayer, and making deb source packages for use with ppa

and yes. you need svn's
all these packages are unsupported for anything but latest svn 

other things that will be added eventually is mplayer with ffmpeg-mt
mplayer-uau 
might make a mplayer-vdpau 
and include zgregs improved libass patched

if there are any packages that breaks due to using libav* from this repository. let me know and i'll see what i can do

it only works on intrepid currently due to hardy having outdated yasm and debhelper
```

deb [http://ppa.launchpad.net/m-frydenlund/ppa/ubuntu](http://ppa.launchpad.net/m-frydenlund/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/m-frydenlund/ppa/ubuntu](http://ppa.launchpad.net/m-frydenlund/ppa/ubuntu) intrepid main

```

---

### Post by mc4man on 2009-03-02
While my main box is already current w/ ffmpeg, libav*', -devs, ect., I just gave your ppa a try on an extra testing machine. So far absolutely no issues.
I'm going to go ahead and build a vlc 1.0 to d.check, but see no reason why it shouldn't work.

The few apps or libs that depend on libavcodec51 (libxine1-ffmpeg, some gstreamer plugins, the repo vlc, ect.) aren't affected as '51 and '52 can co exist.

edit
After a week or so, no issues, vlc built fine ect

---

### Post by heathenx on 2009-04-23
@HolyDuck

f#$%ing thank-you! :)

Now, what are your plans for a jaunty repo?

---

