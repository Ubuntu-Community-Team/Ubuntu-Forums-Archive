---
title: "[SOLVED] MythTV video stuttering XvMC How the heck did that happen..!?"
date: 2007-06-17
forum: Multimedia &amp; Video
---

### Post by NT4usB on 2007-06-17
HD playback has been working fine until a day ago.
Then the video started to stutter... ~ one second intervals, it would pause for a tenth or so, then resume.
Other than the usual updates, I don't touch this box so what happened?
Chased the problem for a couple hours. Backtracked how I got it working in the first place and found that the file I created:
XvMCConfig 
which should contain:
libXvMCNVIDIA_dynamic.so.1 
had somehow been changed and 'li' was chopped off the beginning so it looked like this:
bXvMCNVIDIA_dynamic.so.1

Don't know how it happened... the date on the file was old... like when I originally created it.

I changed the file contents to read libXvMCNVIDIA_dynamic.so.1... stuttering went from one second intervals to ~30 second intervals lasting a second or two. Went through and undid all the other things I had tried, to fix it... UseEvents, NVAGP, etc. and it's playing perfectly again.

Anyway, happy it's working again. Pissed I don't know the cause. Posting this to maybe save some grief for someone else having sudden, mysterious HD playback problems.

---

