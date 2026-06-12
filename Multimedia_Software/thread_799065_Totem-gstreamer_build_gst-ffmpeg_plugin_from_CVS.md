---
title: "Totem-gstreamer: build gst-ffmpeg plugin from CVS"
date: 2008-05-18
forum: Multimedia Software
---

### Post by captaintrav on 2008-05-18
Anyone who has tried playing H264-encoded video in totem might have noticed that playback is really choppy, like your system is too slow (even though CPU usage would not be high whatsoever).  Also, for some reason, (thanks cor2y), video playback of X264, H264, lavc mpeg4, xvid and divx encoded files with Totem in Hardy started to show video artifacts or "pixelizing" for some reason.  

   I'm determined to make totem work well for me, because I really don't like the lack of interface consistency when you use vlc or something else for a video player.  The current "stable" version of gst-ffmpeg is quite old, and there are many bugfixes, in the current source. I'm not a programmer/developer, but I managed to compile the ffmpeg gstreamer plugin from CVS, and it works MUCH MUCH better than the default package for me.  

   I make no guarantees this will work, but if successful, will greatly improve video playback in Totem.  If this refuses to compile for you, or the CVS version gets busted at some point, you can always reinstall the gstreamer0.10-ffmpeg package provided by Ubuntu, so you shouldn't have to worry too much about breaking things.  I'll update the instructions when omissions or issues need to be addressed.

From a terminal session, first of all, remove the default gst-ffmpeg plugin:

```
sudo apt-get remove gstreamer0.10-ffmpeg
```

Install the packages we need to build this thing:

```
sudo apt-get install build-essential libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev liboil0.3-dev automake autoconf cvs subversion libtool libbz2-dev
```

Download the gst-ffmpeg CVS:

```
 cvs -d:pserver:anoncvs@anoncvs.freedesktop.org:/cvs/gstreamer co gst-ffmpeg

```

Then, run the autogen.sh script.

```
cd gst-ffmpeg
./autogen.sh --prefix=/usr

```

Now build and install it.

```
make
sudo make install
```

Now try totem, should play high-definition videos, especially Matroska, much better.

---

### Post by cor2y on 2008-05-18
Do you mean it will do away with the pixelation/visual artifacts of mpeg4 video that popped up in this version of gstreamer?
I'll give this a try and post my results.

---

### Post by cor2y on 2008-05-18
Ok i ran into one error fatal enough to stop configuration the other one not a problem..
1) Make sure the dev versions of gstreamer-plugins-base (libgstreamer-plugins-base0.10-dev) and liboil (liboil0.3-dev) are installed via synaptic without this autogen.sh will halt with an error.

Video playback of X264, H264, lavc mpeg4, xvid and divx encoded files was fixed with the use of the cvs version of gstreamer-ffmpeg no more pixelation/visual artifacts which means when the next version of ubuntu rolls around this will probably be fixed as gstreamer with all its plugins will be updated.
So the choice of waiting or using this fix is yours.

Now all thats left is for gstreamer to have proper dvd video menu navigation and an upgrade to the browser plugin so it at least equals mplayer's and there won't be a need for either totem-xine (dvd menu navigation, chapter navigation etc) and mplayer (browser plugin).

captaintrav thanks and maybe you should have the mods move this to the tutorial section, its a good way to fix the mpeg4 pixelation in totem-gstreamer.

---

### Post by captaintrav on 2008-05-19
> **cor2y said:**
> Ok i ran into one error fatal enough to stop configuration the other one not a problem..
1) Make sure the dev versions of gstreamer-plugins-base (libgstreamer-plugins-base0.10-dev) and liboil (liboil0.3-dev) are installed via synaptic without this autogen.sh will halt with an error.

Video playback of X264, H264, lavc mpeg4, xvid and divx encoded files was fixed with the use of the cvs version of gstreamer-ffmpeg no more pixelation/visual artifacts which means when the next version of ubuntu rolls around this will probably be fixed as gstreamer with all its plugins will be updated.
So the choice of waiting or using this fix is yours.

Now all thats left is for gstreamer to have proper dvd video menu navigation and an upgrade to the browser plugin so it at least equals mplayer's and there won't be a need for either totem-xine (dvd menu navigation, chapter navigation etc) and mplayer (browser plugin).

captaintrav thanks and maybe you should have the mods move this to the tutorial section, its a good way to fix the mpeg4 pixelation in totem-gstreamer.

Thanks for the heads up about the required packages, I'll update the instructions.  I almost forgot about the pixelizing problems that showed up in Hardy, I was chasing other issues that totem-gstreamer has had for a while, namely really choppy playback of H264.  The pixelizing/artifacts can be solved by re-compiling the gst-ffmpeg 0.10.3 from source (I did this), but the released version of gst-ffmpeg source is so outdated by now, it's much better to compile it from CVS.

---

### Post by captaintrav on 2008-05-26
gst-ffmpeg plugin 0.10.4 is now out:

[http://gstreamer.freedesktop.org/news/](http://gstreamer.freedesktop.org/news/)

I compiled the source successfully, and it looks like there is more bug fixes.  Not only do H264 videos play smoothly in totem now, no more sound drifting out of sync.

---

### Post by abelincoln on 2008-06-02
CaptainTrav,

How are the instructions different for installing 0.10.4?

I got the source and was about to do the "unpack, configure, make" thing (sorry, I'm a Windows veteran) but I didn't know if I had to uninstall my original version.  Also, if I install from source I understand it won't be updated with the rest of my software.

Thanks.

---

### Post by captaintrav on 2008-06-02
You would just need to unpack the .10.4, configure, then make, make install.  I would definately still remove the current gstreamer-ffmpeg package, though.   Ubuntu/Debian lib dirs are different than the "standard" I guess, so thus the need for the "--prefix" switch so they are installed to the correct location.  I would expect something like the following: (substitute tar jxvf for zxvf if you downloaded the tarball in .bz)

```

tar zxvf gst-ffmpeg-0.10.4.tar.gz
cd gst-ffmpeg-0.10.4
./configure --prefix=/usr
make
sudo make install

```

You might not have the required development headers though, unfortunately I'm not sure again on which packages you will need, try this:

```
sudo apt-get install build-essential libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev
```

---

### Post by abelincoln on 2008-06-03
Thanks again.

So it's just a normal install and I need to install the development headers because otherwise ubuntu wouldn't know how to 'make' something.

I checked and it looks like I currently have fst-ffmpeg .10.3.  Mplayer plays my h264 video fine but I'm getting the same audio drifting out of sync problem that you describe.  But I understand that mplayer doesn't use gstreamer so this should just be a coincidence.  I guess I'm just hoping that when I go messing around with upgrading my fst-ffmpeg it doesn't break my plan b for video playback.

---

### Post by captaintrav on 2008-06-03
Messing around with the gst-ffmpeg plugin could possibly break any gstreamer apps, like totem and  rhythmbox, but won't break vlc or mplayer as their decoders are internal.  As for the audio drifting out of sync, what video driver are you using?  I've noticed with the nvidia-glx-new driver I was having more problems with this than the nvidia-glx driver.  Unfortunately if you have a newer nvidia card you might need the nvidia-glx-new package.  If you don't have an Nvidia card, I would still try experimenting with the video driver a bit as well, as this can contribute... If you are using Compiz (desktop effects), try switching it off as well.

---

### Post by sensimilla on 2008-06-03
Thanks for the little tutorial. It succesfully compiled and installed for me and I can now watch 720p MKV's without juddering in elisa on my HDTV :guitar:

Only problem is that in totem everyone has turned blue :confused: which is a little bit annoying. It is not a deal breaker as I hardly use totem anyway (I prefer VLC), and the video is fine in elisa. I think I will try compiling the 10.4 version and see if that helps.

How would I update gst-ffmpeg to the latest version from cvs ? I'd rather not download the whole lot again as it takes absolutely ages. Also is it possible to uninstall the current cvs version that I have ?

[Update] 
Well I tried compliling and installing 10.4 and also I reinstalled the 10.3 Ububtu package. I still have blue faces and purple backgrounds so I guess the problem lies elsewhere.

---

### Post by cor2y on 2008-06-24
its the power of the closed nvidia driver :D
They reversed the hue settings in the linux driver, so if you want to see video in the correct color scheme set the hue settings in totem either to the max or minimum settings, that should take care of it.
This only affects you when using the close source nvidia drivers and nvidia has indicated they don't plan to fix it.

---

### Post by captaintrav on 2008-09-02
> **sensimilla said:**
> 

How would I update gst-ffmpeg to the latest version from cvs ? I'd rather not download the whole lot again as it takes absolutely ages. Also is it possible to uninstall the current cvs version that I have ?
\

If you run the cvs checkout command from the directory above where you downloaded it to begin with, it will update the source files, that's the handy thing about using a developer's tool.  On my system, I run:

```
 cvs -d:pserver:anoncvs@anoncvs.freedesktop.org:/cvs/gstreamer co gst-ffmpeg
``` 

Which should result in some output like this:

```
cvs checkout: Updating gst-ffmpeg
U gst-ffmpeg/ChangeLog
U gst-ffmpeg/configure.ac
U gst-ffmpeg/ffmpegrev
etc...
```

After this, you might want to check for a new upstream version of ffmpeg to compile with:

```
cd gst-ffmpeg
./autoregen.sh --prefix=/usr
```

This will update the external dependencies, fetch new updates for them if available, and re-run the configure script.

To answer the second question, to uninstall a version you've built and installed, running "sudo make uninstall" from the gst-ffmpeg directory should clean up what you've installed.  In reality though, the ffmpeg plugins in /usr/lib/gstreamer-0.10/ would just be overwritten by any other version you install, so doing the "make uninstall" thing is probably unnecessary.

---

