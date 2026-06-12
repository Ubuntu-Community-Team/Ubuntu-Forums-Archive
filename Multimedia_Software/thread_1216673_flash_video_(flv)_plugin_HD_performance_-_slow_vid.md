---
title: "flash video (flv) plugin HD performance - slow videos from youtube, megavideo, hulu.."
date: 2009-07-18
forum: Multimedia Software
---

### Post by fm.b on 2009-07-18
hi everyone

i see several posts about the poor performance of the adobe plugin - or the excessive cpu utilization.

two reasons:

* seems always true: adobe flash player doesn't use hardware enabled video acceleration (vdpau for newer Nvidia produts, xvba for ATI), it always relies on the cpu

this is a **major hindrance**, especially for the newest Nvidia ION based "livingroom units" HTPCs - e.g. acer aspire revo, asrock ionstar 330: these things are pretty and relatively cheap, are **very** **capable** in terms of video playback and connectivity, but very underpowered cpu-wise (intel atoms)

some of us are **trying to convince Adobe to do the natural thing**:
[B]
[https://bugs.adobe.com/jira/browse/FP-1152](https://bugs.adobe.com/jira/browse/FP-1152)
[/B]
feel free to vote for the feature request ticket and contribute with your opinion if you please

* sometimes it's because the opengl overlay doesn't get detected, with predictable outcomes. see [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567) - flash optimizations

---

