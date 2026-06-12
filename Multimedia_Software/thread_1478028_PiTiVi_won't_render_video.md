---
title: "PiTiVi won't render video"
date: 2010-05-09
forum: Multimedia Software
---

### Post by billmoseley on 2010-05-09
Hi,

I made a video in PiTiVi and when I go to render it, it says it's rendering, but nothing ever happens.  I've tried several different formats to render in, both audio settings and video settings, but I keep getting the same result.  Any idea how to get a video to actually render?  Thanks!

---

### Post by jethro1138 on 2010-05-13
There's a known bug where pitivi won't render unless you load the project and move the playback head in the timeline. Give that a shot.

I found that while trying to figure out why I can't even move the playback head at all!

---

### Post by sparklyprgs on 2010-06-06
Thanks jethro1138! These are two related bug reports.

[https://bugzilla.gnome.org/show_bug.cgi?id=603102](https://bugzilla.gnome.org/show_bug.cgi?id=603102)
[https://bugs.launchpad.net/ubuntu/+source/pitivi/+bug/503937](https://bugs.launchpad.net/ubuntu/+source/pitivi/+bug/503937)

Moving the timeline indicator fixed the bug for me too. I found the render stops with "1 second to go" displayed, but hitting cancel is OK and the video file plays fine.

Also I found the program crashed / hung 2 or 3 times during about 3 hours of "complex" editing (over 50 clips, cross fading etc). So to avoid pain, SAVE YOUR PROJECT CONSTANTLY! ;-)

---

### Post by fromgi on 2010-06-07
Can someone please explain how I can render multiple video episodes from youtube into a single video episode?

The original video properties are shown in Totem as video: H.264/AVC and audio: MPEG-4 AAC, but I just can't figure how to get Pitiv to render with these properties.  My guess is the even though Pitiv can play these, they can't render with these properties because gstreamer doesn't support them.

Thank you.

---

