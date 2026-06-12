---
title: "Gutsy and Gstreamer plugins"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by Southtown on 2007-10-20
I tried to install the "Gstreamer Extra Plugins" via the "Add/Remove" but got an error.

[SIZE="1"]"Cannot install 'gstreamer0.10-plugins-ugly'
This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.
Switch to the 'synaptic' package manager to resolve this conflict."[/SIZE]

But Synaptic says:

[SIZE="1"]gstreamer0.10-plugins-ugly:
 Depends: libid3tag0 (>=0.15.1b) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable[/SIZE]

The same goes for 'gstreamer0.10-plugins-bad' and 'gstreamer0.10-plugins-bad-multiverse' required by 'GStreamer plugins for mms, wavpack, quicktime, musepack' and 'GStreamer plugins for aac, xvid, mpeg2, faad', respectively. Any suggestions regarding gstreamer and gutsy would be greatly appreciated.

---

### Post by cjm5229 on 2007-10-20
Try removing Movie Player (Xine) and go back to Movie Player. Movie player (Xine) Conflicts with most of the codecs.

---

### Post by strawman on 2007-10-21
did you try a 'sudo apt-get update' ?  this worked for me

---

### Post by dcoffey48 on 2007-10-26
I am having the same problems.

Any solutions yet?

Dave.

---

### Post by Deakon on 2007-10-26
install vlc and go ez mode

---

### Post by ryanshaw on 2007-11-06
I had the identical problems as others such as not being able to install syslinux.  Didn't think they were related but this post fixed them both.

Repositories Gutsy 7.10
[http://ubuntuforums.org/showthread.php?p=3720928#post3720928]("http://ubuntuforums.org/showthread.php?p=3720928#post3720928")


Ryan

---

### Post by Quang Sang on 2007-11-13
I'm a new beginner, i just use ubuntu a month, i also met this problem. Now I have solved this problem, thank you for everybody.

---

