---
title: "Can't run SC2 on max graphics with wine - is this expected?"
date: 2013-03-05
forum: Multimedia Software
---

### Post by Webnet on 2013-03-05
I recognize that I'm using Wine and that will have an effect on things.  I thought I'd ask anyways to see if I might be doing something wrong.

On Windows I can run my graphics on Ultra without any problems at all.  On Ubuntu 12.10 it takes a while to load the game, but once it's loaded everything's fine - as long as my graphics are turned down to low. I am running 64 bit.

OpenGL version string: 4.2.0 NVIDIA 304.43

*"lspci -v | less"* output is:
```
01:00.0 VGA compatible controller: NVIDIA Corporation GF104 [GeForce GTX 460] (rev a1) (prog-if 00 [VGA controller])
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at fc000000 (32-bit, non-prefetchable) [size=32M]
        Memory at d8000000 (64-bit, prefetchable) [size=128M]
        Memory at d4000000 (64-bit, prefetchable) [size=64M]
        I/O ports at cc00 [size=128]
        [virtual] Expansion ROM at fe980000 [disabled] [size=512K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia_current, nvidia, nouveau, nvidiafb

```
[IMG]http://postimage.org/image/mw2bhx77f/[/IMG]

---

### Post by Mark Phelps on 2013-03-05
Wine is basically a set of custom-written DLLs that replace Windows system calls with Linux system calls.

It has nothing whatsoever to do with the drivers in use.  Some folks mistakenly think you can install Windows video drivers using wine; they're wrong.

If you can't get the resolution you want and/or the frame rate you want, it could be because the drivers in Windows that can do that, simply aren't available  (or available anymore) in Linux.

Sorry, not an Nvidia person, so I can't advise you on this driver.

---

### Post by Webnet on 2013-03-05
Thanks for the insight into how Wine works.  I'm currently using **nvidia-current**.  I tried the drivers from NVidia's site but had some trouble with them - though now I can't remember what that trouble was.  It was like 3-4 weeks ago now.

---

