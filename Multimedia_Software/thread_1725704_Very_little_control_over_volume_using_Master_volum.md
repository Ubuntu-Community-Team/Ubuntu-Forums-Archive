---
title: "Very little control over volume using Master volume level"
date: 2011-04-10
forum: Multimedia Software
---

### Post by fekauffman on 2011-04-10
Hi, All--

I'm new to Ubuntu, but have been able to work my way through most of the issues I've had so far. The one that is confounding me right now is this:

My volume control seems to have only three settings: TOO LOUD, VERY QUIET, OFF. If I adjust the Master volume slider from the Panel, only about the right 1/8th has any effect and if I slide it past about the 95% mark, I get no sound at all. At the far-right end of the volume control, I get total volume. It's basically like the slider only has any impact in the top 5% of it's space. Below 95% of the slide, there is zero volume.

It's so drastic, that one tap down of the volume button on my keyboard kills the sound (because it nudges the slider past that 95% mark).

This happens in the Audio settings, etc., system-wide. If I adjust the volume for an individual app from within the app (MPlayer, for example) it behaves exactly as expected (that is, app volume works smoothly, it's just master volume that has this issue).

I have run through most of the "obvious" things-- I'm wondering if I broke something by installing the extra KDE packages to get Amarok to work.

I've done a lot of searching, but could not find anyone else reporting this problem.

---

### Post by lidex on 2011-04-10
Check "Volume range anomalies" on this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

---

### Post by fekauffman on 2011-04-10
That worked!

Not exactly perfect, but at least I have some variability in the volume range and I know where to keep digging.

Thank you for your support!

Fletcher

---

### Post by lidex on 2011-04-10
Great. This may shed some light:
[http://ubuntuforums.org/showthread.php?t=1317562](http://ubuntuforums.org/showthread.php?t=1317562)

---

