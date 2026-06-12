---
title: "compiling gstreamer0.10-plugins-bad"
date: 2010-01-22
forum: Multimedia Software
---

### Post by prince.buster on 2010-01-22
Has anyone here managed to compile gstreamer0.10-plugins-bad?

I did it in ubuntu for 0.10.17 without errors, but the plugins don't show up in gst-inspect.

The plugins from the good and ugly packages are there - so I am able to play mp3's and whatnot. But I particularly wanted to experiment with the latest jackaudiosink. The libraries exist on the system:

```
jez@X31:~/gst-plugins-bad-0.10.17$ gst-inspect | grep jack
jez@X31:~/gst-plugins-bad-0.10.17$ locate gstreamer | grep jack
/usr/local/lib/gstreamer-0.10/libgstjack.la
/usr/local/lib/gstreamer-0.10/libgstjack.so
jez@X31:~/gst-plugins-bad-0.10.17$ gst-inspect --gst-version
GStreamer Core Library version 0.10.25

```

Is there some post-installation step that I have missed?

---

### Post by Yellow Pasque on 2010-01-22
You may need to run sudo ldconfig
There's also a PPA for the latest gstreamer: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by mc4man on 2010-01-22
If you're having any continuing issues after a ldconfig you may want to try the ppa mentioned
While I'd previously done a couple of the new gst plugins on karmic, went ahead and added that ppa and upgraded the rest.
Works quite fine.

Also of interest is that while Xv is what I use, the ppa has an OpenGL plugin for gstreamer that may benefit some. (also tested that and no issues

---

### Post by prince.buster on 2010-01-22
I've narrowed it down to the fact that the custom-compiled libraries have been installed to /usr/local/lib/* instead of /usr/lib/*.

Still not sure what to do about it. Tried adding /usr/local/lib to /etc/ld.so.conf and running sudo ldconfig, but gstreamer could still not find the plugins.

Also tried export GST_PLUGIN_PATH=/usr/local/lib/gstreamer-0.10/ . It found some of the new plugins but some of the old ones were missing. Does GST_PLUGIN_PATH override all the other paths? Also, is there a configuration file where the default plugin search paths can be set?

---

### Post by mc4man on 2010-01-22
Honestly, if you were to build gst plugins I think it's far better to do as a package set as normally done. 

Not that hard to do, in this case you have everything needed available to use the karmic .diff with the exception of libgme0 (& -dev).
Considering gme borders on who cares you could edit it out or just grab and install the lucid package(s) 

But that ppa is just as good and already done, I'd go that route ( unless there is something not built in to it that you need (unlikely

screen is ex. of way to build. ppa is way to go

---

### Post by prince.buster on 2010-01-22
thanks, that PPA was the way to go!

still curious why the ldconfig or GST_PLUGIN_PATH didn't work, though.

---

### Post by prince.buster on 2010-01-22
what do you mean "a package set"? do you mean it would be easier to compile all the gstreamer software at once, including the good, ugly and base packages?

The Personal Package Archive is definitely the easiest way to get up-to-date packages, but compiling can teach you a lot :-) and adds valuable discussion to the forums!

thanks heaps, though

---

