---
title: "White Noise and Low Quality Sound"
date: 2010-08-04
forum: Multimedia Software
---

### Post by Dereks Sound on 2010-08-04
Hello, I recently installed Ubuntu on my Clevo D901c laptop and have run into a slight problem. When I turn my sound up all the way I hear a white noise or "staticy" sound which I do not know how to get rid of. My sound when playing music is not the best sound quality either. Please help me out somebody please. Here is my sound card info: 

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
    Subsystem: CLEVO/KAPOK Computer Device 0902
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at e4500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

Thanks in advance. ):P

---

### Post by neogenesis59 on 2010-08-04
I also had the low quality of sound with PulseAudio and I found this thread on the forums:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Here a small section is about increasing the quality of PulseAudio. It states that you have to change the settings in /etc/pulse/daemon.conf and for example change the part : 
```
resample-method = [COLOR=Blue]speex-float-1[/COLOR]
```Into for example:

```

resample-method = src-sinc-medium-quality

```Hope it helps. The section in the post is located in the Q&A of Appendix B.

---

### Post by Dereks Sound on 2010-08-04
I tried your suggestion and the problem persists. Low quality sound and white noise in the background.

---

