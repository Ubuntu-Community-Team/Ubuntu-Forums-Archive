---
title: "'hal' for vlc? why?"
date: 2008-01-21
forum: Multimedia &amp; Video
---

### Post by r0ck80y on 2008-01-21
Hi,

I wanted to know what is the importance of 'hal' for vlc compilation? Any comments?
And also how do i check what features are enabled/disabled in my vlc player in ubuntu (like as in gentoo language, what USE flags does my vlc use)??
Thanks

---

### Post by banewman on 2008-01-21
Hal (hardware abstraction layer if I'm correct) is needed so vlc will find the sound card and video card - and dbus for the use flags - I don't know offhand how to get that info tho.
:)

---

### Post by disturbed1 on 2008-01-21
> **r0ck80y said:**
> Hi,

And also how do i check what features are enabled/disabled in my vlc player in ubuntu (like as in gentoo language, what USE flags does my vlc use)??
Thanks


vlc -l  prints a list of available modules
-p, --module <string>          print help on a specific module (can be combined with --advanced)

vlc -h to see vlc help.

---

