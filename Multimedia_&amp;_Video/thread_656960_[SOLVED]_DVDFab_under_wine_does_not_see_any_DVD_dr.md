---
title: "[SOLVED] DVDFab under wine does not see any DVD drive"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by peterdm on 2008-01-03
For a couple of days I've been struggling with dvdfab under wine, and I've found a solution that maybe can save some people out there some time.

Installation and everything were successful, but the problem was that dvdfab did not see any dvd drive.
It worked fine back when I was still running opensuse 10.3, so I was convinced that I could make it work under gutsy as well.
The solution turned out to be much simpler than some info on the internet led me to to believe.

The *only* thing I had to do is open "wine"->"configure wine", select the "drives" tab and hit "autodetect".

Apparently this is not done automatically upon installation (a possible bug in the wine package?).

At first I was led astray by some info I had found in older posts where I had to download and copy mfc42.dll and set up wine to use it. This was all totally besides the point in my case.

Cheers,

Peter

---

### Post by ejs7597 on 2008-01-06
What version of DVDFAB did you install?  I have been using 3.2.0.1 for quite a while, but I tried to install version 4 today, and can't get the registration to work, I even got a new registration number for version 4.

---

