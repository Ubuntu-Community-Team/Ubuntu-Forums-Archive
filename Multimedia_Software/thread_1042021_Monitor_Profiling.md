---
title: "Monitor Profiling"
date: 2009-01-17
forum: Multimedia Software
---

### Post by BlackMaxPhoto on 2009-01-17
Is there a deb package monitor profiling/calibration solution available for Ubuntu Studio?

:confused:

---

### Post by dargaud on 2009-02-08
Good question. I'm also interested in what monitor calibration tools are available. Support for Datacolor Spyder probes (both monitor and printer probes) ? Can you use a print profile when printing from any app ?

I guess the basics start here:
```
sudo aptitude install icc-profiles liblcms liblcms-utils xicc xcalib lprof
```

The easiest is to use a profile generated under Windows:
```
xcalib "/home/dargaud/c/WINDOWS/system32/spool/drivers/color/DoubleSight__DS-240WB-30-30.icm"
```

I also tried lprof and couldn't figure out how to load an existing icm file...
But there's a lengthy discussion [here]("http://ubuntuforums.org/showthread.php?t=1002362") with a lot more info...

---

