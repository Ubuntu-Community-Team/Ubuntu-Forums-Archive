---
title: "Pitivi crashes frequently"
date: 2014-06-03
forum: Multimedia Software
---

### Post by angelsguitar on 2014-06-03
Hi.

I'm trying out Pitivi on Lubuntu 14.04.  At first it opens without problems, but when I try to add videos and put them on the timeline, Pitivi freezes completely.  After I kill the program, it freezes completely if I try to repoen it.

This is the output on the terminal when it freezes:
```
Missing soft dependency:
- pycanberra not found on the system
    -> enables sound notifications when rendering is complete
ERROR:root:Could not find any typelib for GnomeDesktop
Missing soft dependency:
- GnomeDesktop not found on the system
    -> file thumbnails provided by GNOME's thumbnailers

(pitivi:3006): Gdk-WARNING **: gdk_window_set_icon_list: icons too large
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:523: Warning: Source ID 39 was not found when attempting to remove it
  super(MainLoop, self).run()
Terminated

```

I can't find any package called "pycanberra" (maybe is part of another package with a different name?).

Also, there's no package called "GnomeDesktop".  I suppose it refers to the Gnome package.  But installing Gnome just to solve this doesn't seem to be the way to go for me - I'm using LXDE.

Any idea why the program is so unstable?  Any suggestions on how I may fix it?  Thanks in advance.

---

### Post by tgalati4 on 2014-06-03
Try *openshot*.

---

### Post by angelsguitar on 2014-06-03
Yes, I am already using *Openshot*.  Great NLiVE.  

But still would like to try out Pitivi, just out of curiosity.

---

### Post by tgalati4 on 2014-06-03
Try pitivi in a gnome2 environment.  It is obviously having problems with 14.04's Gnome3 libraries and notification system.  That would suggest filing a bug with the developers.

---

### Post by angelsguitar on 2014-06-04
tgalati4, do you mean to try to run it on MATE, for example?

---

### Post by tgalati4 on 2014-06-04
You could try running it in MATE which is based on gnome2 or any 12.04 system (with gnome2 and gnome3 libraries) and see if it works correctly.  I haven't used *pitivi* in years and I'm not running 14.04 yet, so I can't troubleshoot a 14.04 issue.

I don't have pycanberra on my Linux Mint MATE (based on 12.10) system, but there is a canberra library:

> tgalati4@Mint14-Extensa ~ $ apt-cache search canberra
gnome-session-canberra - GNOME session log in and log out sound events
libcanberra-dev - simple abstract interface for playing event sounds
libcanberra-doc - simple abstract interface for playing event sounds - doc
libcanberra-gstreamer - GStreamer backend for libcanberra
libcanberra-gstreamer-dbg - GStreamer libcanberra backend detached debugging symbols
libcanberra-gtk-common-dev - simple abstract interface for playing event sounds
libcanberra-gtk-dev - simple abstract interface for playing event sounds
libcanberra-gtk-module - translates GTK+ widgets signals to event sounds
libcanberra-gtk-module-dbg - libcanberra GtkModule detached debugging symbols
libcanberra-gtk0 - GTK+ helper for playing widget event sounds with libcanberra
libcanberra-gtk0-dbg - libcanberra-gtk libraries detached debugging symbols
libcanberra-gtk3-0 - GTK+ 3.0 helper for playing widget event sounds with libcanberra
libcanberra-gtk3-0-dbg - libcanberra-gtk libraries detached debugging symbols
libcanberra-gtk3-dev - simple abstract interface for playing event sounds
libcanberra-gtk3-module - translates GTK3 widgets signals to event sounds
libcanberra-gtk3-module-dbg - libcanberra GtkModule detached debugging symbols
libcanberra-pulse - PulseAudio backend for libcanberra
libcanberra-pulse-dbg - PulseAudio libcanberra backend detached debugging symbols
libcanberra0 - simple abstract interface for playing event sounds
libcanberra0-dbg - libcanberra libraries detached debugging symbols
fso-deviced-player-canberra - Canberra player module for fso-deviced
python-mlpy - high-performance Python package for predictive modeling


---

### Post by anilduggirala-t on 2014-08-13
The same exact thing is happening to me with Pitivi in Lubuntu 14.04. Will try Openshot instead. Can someone tell me how one goes about filling a bug in this case?
thanks,

---

