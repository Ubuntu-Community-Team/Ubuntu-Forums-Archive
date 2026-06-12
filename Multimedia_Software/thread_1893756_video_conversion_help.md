---
title: "video conversion help"
date: 2011-12-11
forum: Multimedia Software
---

### Post by GrumpyOldGoat on 2011-12-11
I bought a harbor freight video security system that backs up 'event' as *.264.  The unit came with a mini Cd that has an "AVIGenerator" program that converts 1 file at a time. (it runs strictly on windoze)
I have several thousand files to convert.  I have a stand alone windows computer that is not connected to the internet that I am using currently, but all the 'converters seem to require internet connection which is not possible due to its location.

I would much prefer to use this computer (AMD quad core 8Gigs of ram) running Ubuntu 11.04.

Any ideas and instruction for installing?

Thank You

---

### Post by papibe on 2011-12-11
You can easily convert those videos using the GUI program called WinFF, or get an even fine tuning conversion using ffmpeg (command line program).

Hope it helps.
Regards.

---

### Post by GrumpyOldGoat on 2011-12-11
"Not a recognized video file"

Here is a sample file of the raw data and the 'converted' file using the supplied ---one file at a time--- program that came with the system.

Well, that lacked a 'security token'....

I think I'll go have a nice headache for a while and check back tomorrow...

Thank You for the suggestion, and I'm fairly certain I will use the program you recommended.

---

### Post by FakeOutdoorsman on 2011-12-11
What does FFmpeg say about one of the videos?
```
ffmpeg -i input.264
```

---

