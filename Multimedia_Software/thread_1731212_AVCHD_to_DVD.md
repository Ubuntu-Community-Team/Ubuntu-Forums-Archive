---
title: "AVCHD to DVD?"
date: 2011-04-16
forum: Multimedia Software
---

### Post by analogcolors on 2011-04-16
For National Record Store Day (today!) my local record shop put on a half-hour concert featuring a small, obscure (but good!) local band. I filmed their set for them, and was planning to burn it to DVD. Five copies - one for each of the three band members, one for the owner of the record store, and one for myself. Easy, right? Wrong.
I have no idea what to do! My camera (in the interest of specifics, a Sony HDR-CX110) records in the *.mts format, which has proved to be somewhat problemeatic: I can't burn the two *.mts files I recorded straight to DVD, because they're not in the native DVD file structure (VIDEO_TS/VTS_01_1.VOB etc). When I try to use Brasero to burn the disk, I get told to install a package which doesn't exist (at any rate, nothing comes up when searching for it), and I have no idea where to go from here. [SIZE="4"]arrrgh![/SIZE]

---

### Post by BicyclerBoy on 2011-04-16
AVCHD is m2ts container. is a modified mpeg2-ts format.

The video (& audio) encoding (H264/MPEG4/10) is not compatible with DVD.

You should be able to use AviDemux to convert to mpeg2-ps format (DVD) mpeg2 video with LPCM or mp2 or AC3 audio.

Ffmpeg (GUI WinFF)  or Handbrake should be able.

People have had problems with m2ts streams from some cameras because of odd inconsistencies in time stamp info.  (non-monotonic PTS etc)
So it could pay to try recent build of Handbrake & Avidemux.

---

