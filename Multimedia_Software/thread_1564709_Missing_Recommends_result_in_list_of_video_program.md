---
title: "Missing Recommends result in list of video programs  to be removed?"
date: 2010-08-30
forum: Multimedia Software
---

### Post by ubuntu1sttimer on 2010-08-30
Have 10.04 upgraded from 9.10. Before the upgrade I had Ubuntu Studio installed on 9.10 and removed it. 

Now when I check Synaptic for Missing Recommends it lists:

libavcodec52
libavformat52
libavutil49

They appear to be video related. When I check them I get a long list of files to be deleted. The list to be deleted is the same for each of the three files and is shown at the end of this post.

It does not appear wise to allow this to happen. Do I need the files that it tells me I need? If so, is there a way to get around all the removals that I also need many of. Most of what I want to do is capture video, edit it, and write it to DVD. Seems to be a major project to get that working.

audacious
audacious-plugins
blender
dvd-slideshow
ffmpeg
ffmpeg2theora
freemixs
frei)r-plugins
gem
gstreamer0.10-ffmpeg
kdenlive
kino
libavcodec-extra-52
libavcodec-unstripped-52
libavdevice-extra-52
libavdevice-unstripped-52
libavformat-extra-52
libavformat-unstripped-52
libavifile-0.7c2
libcv4
libcvaux4
libhighgui4
libmit++3
libmit2
lives
melt
mencoder
mplayer
mplayer-nogui
openshot
python-mlt2
qdvdauthor
transcode
ubuntustudio-audio
ubuntustudio-graphics
ubuntustudio-video
vlc
vlc-nox
vic-plugin-pulse
xjadeo

---

### Post by Deadite81 on 2010-08-30
Synaptic isn't as "smart" as you might think.  In my opinion, the missing recommends area is more misleading than anything else.  I don't know exactly what it bases it's criteria on, but I assume it's relating to whatever desktop "meta-package" you are using, which can get very confusing if install stuff from other repos and distros.

The packages you are supposedly missing (libavcodec52, libavformat52, libavutil49) are not actually missing.  I know, it's confusing.

libavcodec52 = libavcodec-extra-52
libavformat52 = libavformat-extra-52
libavutil49 = no other depends installed(?)

Why it does this I don't know, but mine is full of stuff (Evolution, F-Spot, etc.), including the packages in yours.  Perhaps Synaptic will institute some sort of "learning" mechanism, but until then, if you deviate from your vanilla install too much be prepared to have at least a few "missing recommends".  I even get "orphaned" files occasionally that are in fact NOT orphaned, which I have to correct with the command line so as not to accidentally remove them!  Sometimes your judgement is smarter than the machine.

Hope this helps!

---

### Post by ubuntu1sttimer on 2010-08-31
Thanks for the info. I wondered about that. Had seen the list  before but just ignored it. As I am having a number of video capture problems, I was starting to wonder if it could be related. Have learned that it is not all that hard to break things.

Again, thanks for the information.

---

### Post by Deadite81 on 2010-08-31
I recently encountered video related problems.  It had to do with ffmpeg, mencoder, and mplayer not getting along correctly.  This thread helped me, perhaps you can benefit from it as well: [http://ubuntuforums.org/showthread.php?p=9769063#post9769063](http://ubuntuforums.org/showthread.php?p=9769063#post9769063)

Also, VLC can cause lots of problems if not installed from a reliable source.  If that's where your problems arise you may want to look into getting the latest version (1.1.4):
[http://www.webupd8.org/2010/08/install-vlc-114-in-ubuntu-via-new-ppa.html](http://www.webupd8.org/2010/08/install-vlc-114-in-ubuntu-via-new-ppa.html)

Good Luck!

---

