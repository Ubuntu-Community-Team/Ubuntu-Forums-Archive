---
title: "Banshee crashes when trying to play videos"
date: 2009-10-28
forum: Multimedia Software
---

### Post by rdoolen on 2009-10-28
I am using Banshee 1.6 Beta 2 (1.5.1) on Karmic. It seems to work fine except if I try to play a video it crashes (completely disappears). If I start Banshee from the command line, I get a long series of errors which ends with:

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

I can post everything if its helpful.

This happens to me on two different machines, both with 9.10, one 32 bit, one 64bit. It seems to happen on every video format: avi, mp4, mov etc.

I have tried un-installing and reinstalling Banshee as well as many (if not all) the mono runtime libraries.

Has anyone else seen this? Have any suggestions?

Thanks!

---

### Post by directhex on 2009-10-28
File a bug with the full stacktrace

---

### Post by nerdelicious on 2009-11-21
I'm experiencing the same behavior. Banshee 1.5.1 on 64 bit Karmic.

Any news on this? Did you file a bug report?

---

### Post by rdoolen on 2009-11-21
I never did file a bug report. 

I fixed it by using vlc for videos.

---

### Post by NO2 on 2010-01-30
play an audio file before a video, it works fine after that

---

### Post by Another Monkey on 2010-02-05
There was a bug logged for this recently
[https://bugzilla.gnome.org/show_bug.cgi?id=609060](https://bugzilla.gnome.org/show_bug.cgi?id=609060)

If you can provide other information (traces etc) then it might be an idea to do so.

---

