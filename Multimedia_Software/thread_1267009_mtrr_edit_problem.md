---
title: "mtrr edit problem"
date: 2009-09-15
forum: Multimedia Software
---

### Post by wenhaosparty on 2009-09-15
I am using Jaunty. I noticed the full screen flash playback is quite choppy and it has already been reported as a bug, solution to the problem has also been posted:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/314928/](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/314928/)

When implementing the solution, when the last step:
```
echo "base=0xb0000000 size=0x10000000 type=write-combining" > /proc/mtrr
```

I keeps getting:
```
bash: echo: write error: Invalid argument
```
when trying to edit mtrr file.

Anyone knows why?

---

