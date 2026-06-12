---
title: "non-smooth playback of H.264 video files"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by F for Fragging on 2007-11-05
Please see [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/121279](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/121279) and [http://bugzilla.gnome.org/show_bug.cgi?id=482660](http://bugzilla.gnome.org/show_bug.cgi?id=482660)

I'm very disappointed that Ubuntu Gutsy was released with this bug. However, I was very surprised that only three people including myself responded to this bugreport. Shouldn't everyone who tries to play video files encoded in H.264 with totem-gstreamer experience this bug, or is everybody using anything other than totem-gstreamer to play back their video files? Who else can reproduce the problem?

---

### Post by el mariachi on 2007-11-05
Mplayer doesn't show this bug.. maybe that's why only 3 people posted it.

---

### Post by sonofusion82 on 2007-11-05
haha.. for me.. my PC is too slow to play HD resolution H.264 videos anyway.

---

### Post by mirzmaster on 2007-12-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/121279](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/121279) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				F, thank you for posting this issue to these forums.  I've been experiencing the same horrid H.264 playback and was unable to find that it was a reported issue.  I earlier thought it was a problem with playback relating to the .mkv container format, but apparently it's with the H.264 code instead.

So thanks for posting the bug links.

Btw, I find that telling people to use mplayer instead of totem is a common workaround to video playback issues in Ubuntu, but one that should be unacceptable.  If totem-gstreamer is the default media player, that's what the vast majority of users will be utilising, and the expectation is that it should provide smooth HD video playback.

Well, at least the bug is reported.  :)  I'll be keeping my fingers crossed for an update!

---

### Post by reets on 2008-01-10
I have this same problem in VLC, video freezes for a few seconds and sound continues. Does it a lot though during a movie :(

---

### Post by el mariachi on 2008-01-12
All hail the mighty Mplayer :D

---

### Post by cyberstven on 2008-01-15
Just wanted to bump and say I am having the same issue.  I signed up to these forums to figure out how to resolve it!

---

### Post by reets on 2008-01-16
Mplayer FTW for sure. Installed it and played with the settings and it works perfectly! The easy option was to enable frame dropping but the videos were slightly jaggy.

What worked for me was Enabling double buffer, direct render, turning off post-process option, and maxing out the cache (65535 i think it was). Thanx for the suggestion to try it !!!

---

### Post by nexu56 on 2008-02-23
Unfortunately for me, I am getting this problem on my media center, which runs Elisa, which uses gstreamer only, so MPlayer is not an option #-o

---

