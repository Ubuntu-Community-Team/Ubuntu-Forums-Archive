---
title: "Conflict between gstreamer0.10-plugins-bad and gstreamer0.10-fluendo-mpegdemux"
date: 2009-04-25
forum: Multimedia Software
---

### Post by stopthewar24 on 2009-04-25
Hi,

I recently installed 9.04 (via online upgrade over 8.10), and am running into a weird issue with the gstreamer0.10-plugins-bad package.  Specifically, this package shows up in the Upgrade Manager as "greyed-out" and unchecked -- it indicates that an update is available but not able to be installed.  When I look up the gstreamer0.10-plugins-bad package in Synaptic, it indicates that an update is available but installing it would require the removal of gstreamer0.10-fluendo-mpegdemux.  Is there a reason why these two are conflicting?  Is there one that would be better to keep?

My version of gstreamer0.10-plugins-bad is 0.10.8-1 (not current).
My version of gstreamer0.10-fluendo-mpegdemux is 0.10.15-1 (current).

Thanks for your thoughts!

---

### Post by mc4man on 2009-04-25
Don't have jaunty but there shouldn't be a conflict if you wanted them both (or 3, there are 2 fluendo packages (one muxes, one demuxes

I'd go ahead and uninstall the fluendo package, update your gstreamer ugly and then add back the fluendo if desired

---

### Post by stopthewar24 on 2009-04-25
Right, I did that (removed fluendo and upgraded plugins-bad) and things seem to be working.  Fluendo won't reinstall, though -- it wants to remove plugins-bad beforehand.  When I do that (keep fluendo and ditch plugins-bad) I lose a good deal of media format support, but with only plugins-bad installed, I seem to have the full set of functionality as far as I can tell.  I don't know exactly why fluendo was on there in the first place, actually.  For now, I'll keep it this way barring any future issues cropping up.  Thanks for your help!  I appreciate it.

---

### Post by mc4man on 2009-04-26
just checking off of a live cd if you install the *multiverse* variants of the ugly and bad then there isn't a conflict.
There will be with the 'normal' versions though

The multiverse have more capabilities and are the preferred versions

(though probably no big loss with the fluendo anyway (enable ts (transport streams - I think related to digitial brodcast streams (dvb

> Commit Log for Sun Apr 26 09:05:52 2009


Installed the following packages:
gstreamer0.10-plugins-bad-multiverse (0.10.11-0ubuntu1)
libfaac0 (1.26-0.1ubuntu2)
libmjpegtools-1.9 (1:1.9.0-0.0)
libquicktime1 (2:1.1.0+debian-1build1)
libxvidcore4 (2:1.1.2-0.1ubuntu3)
gstreamer0.10-plugins-ugly-multiverse (0.10.7-2)
libmp3lame0 (3.98-0.0)
gstreamer0.10-fluendo-mpegdemux (0.10.15-1)
gstreamer0.10-fluendo-mpegmux (0.10.4-1)
libtsmux0 (0.3.0-1)
gstreamer0.10-ffmpeg (0.10.6.2-1ubuntu2)
gstreamer0.10-plugins-ugly (0.10.10.2-1build1)
libsidplay1 (1.36.59-5)
gstreamer0.10-pitfdll (0.9.1.1+cvs20080215-1ubuntu1)



---

### Post by stopthewar24 on 2009-04-26
Thanks.  That's true; the multiverse version removes the conflict.  However, it also removed AAC playback capability on my computer, so I'm adding the universe version of gstreamer0.10-plugins-bad back on and removing fluendo again.  Looking at the changelog for the multiverse package, this might be the reason...

```
gst-plugins-bad-multiverse0.10 (0.10.5-2) hardy; urgency=low

  [ Emilio Pozuelo Monfort ]
  * debian/control,
    debian/gstreamer-plugins-bad-multiverse.install:
    - Remove libfaad2-dev from Build-Depends. The faad plugin is now
      included in gstreamer0.10-plugins-bad, since it has been moved to
      the universe repository.

  [ Sebastian Dröge ]
  * debian/build-deps.in:
    + Really remove faad.

 -- Sebastian Dröge <slomo@ubuntu.com>  Sun, 25 Nov 2007 18:39:25 +0100
```


For now, I'm fine without the fluendo, and with keeping both the universe and multiverse versions of plugins-bad.  This seems to work.

---

### Post by mc4man on 2009-04-26
```
Looking at the changelog for the multiverse package
```
Interesting, looks like they've changed some things for jaunty, good to know. (I'm still using hardy, but i'm sure this will come up in some fashion for someone else

---

### Post by jnorth on 2009-05-05
> **mc4man said:**
> ```
Looking at the changelog for the multiverse package
```Interesting, looks like they've changed some things for jaunty, good to know. (I'm still using hardy, but i'm sure this will come up in some fashion for someone else
Just came up for me... my dev mythtv frontend is running jaunty and I'm playing around wiht Gloss, an alternate myth frontend.  It requires both as dependencies...

Playing around now to see how I can get around it, I'll probably just try an install from source with the plugins-bad installed.

---

### Post by zeus77 on 2010-05-27
Anyone ever come up with a fix for this?  This has been a problem in the last few version of Ubuntu, and still exists in 10.04 (lucid).

I need gstreamer0.10-plugins-bad for playing a bunch of different non-free media types... and gstreamer0.10-fluendo-mpegdemux is needed for watching things I've recorded with MythTV.

Hmmmm...

---

