---
title: "confused about media players and codecs"
date: 2007-12-20
forum: Multimedia &amp; Video
---

### Post by erfahren on 2007-12-20
I know this has been asked before, but after everything I've read about this I'm only a little less confused.

Everytime I do a fresh install of Ubuntu I start wondering about this again.

I've already discovered that VLC and the mozilla-vlc-plugin works better for me that the mozilla-totem-plugin. 

On a fresh install I usually get:
[i]gstreamer0.10-ffmpeg
gstreamer0.10-plugins-bad 
gstreamer0.10-plugins-bad-multiverse 
gstreamer0.10-plugins-ugly 
gstreamer0.10-plugins-ugly-multiverse[/i] 

and the *w32codecs*

my questions:
are the w32codecs only used with MPlayer?  (I don't really use or install mplayer anymore)

are the "gstreamer0.10-plugins-bad" and  "gstreamer0.10-plugins-bad-multiverse" really needed? They aren't included in ubuntu-restricted-extras

the gstreamer codecs are used with totem, aren't they? (only with totem?)

I'd like to get all this straightened out in my mind once and for all. Any explanations of this would be helpful. thanks!

---

### Post by coskierken on 2007-12-20
Ok, if you want an easy way to do this, due a search for ubackup! or it might now be called Quickstart.  My buddy wrote it to solve the problems he had with backups and for the problems we had with the codes.  It is a system backup utility and more with utilities for the codec and installing other useful programs.  It is great.  :lolflag:

---

### Post by erfahren on 2007-12-20
> **coskierken said:**
> Ok, if you want an easy way to do this, due a search for ubackup! or it might now be called Quickstart.  My buddy wrote it to solve the problems he had with backups and for the problems we had with the codes.  It is a system backup utility and more with utilities for the codec and installing other useful programs.  It is great.  :lolflag:
I'm not looking for something like that. I just wanted to get this stuff sorted out in my mind.

thanks anyway

---

### Post by Samhain13 on 2007-12-20
This may be of help [http://gstreamer.freedesktop.org/apps/](http://gstreamer.freedesktop.org/apps/). :)

I don't see VLC in the list of applications that use GStreamer so I'm guessing that it comes with its own codecs.

---

