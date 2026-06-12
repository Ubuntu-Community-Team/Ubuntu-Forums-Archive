---
title: "Glxgears not showing FPS"
date: 2009-11-29
forum: Multimedia Software
---

### Post by Raffles10 on 2009-11-29
Since installing Karmic x86_64 glxgears no longer prints fps:

ubuntu 9.10
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
33750 frames in 5.0 seconds
34524 frames in 5.0 seconds
33937 frames in 5.0 seconds
34528 frames in 5.0 seconds

Mint 8 (ubuntu 9.04)
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
34156 frames in 5.0 seconds = 6831.169 FPS
28867 frames in 5.0 seconds = 5773.310 FPS
35831 frames in 5.0 seconds = 7166.160 FPS
35847 frames in 5.0 seconds = 7169.261 FPS

I found this bug report:

[Bug #449263]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/449263")

Which says:

> Too many people were abusing it in bug reports. They got confused that since it prints 'fps' that it must be a performance benchmark, which it is not. Removing the fps calculations is to stop the misuse.

Are they serious ? Does anyone using Karmic get a fps printout ? If it has been removed this is treating Ubuntu users like children. Do they think that no Ubuntu users are intelligent enough to know the difference between glxgears and proper benchmarking tests ? :shock:

---

