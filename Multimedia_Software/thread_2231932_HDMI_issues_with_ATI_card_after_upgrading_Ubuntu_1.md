---
title: "HDMI issues with ATI card after upgrading Ubuntu 14.04"
date: 2014-06-28
forum: Multimedia Software
---

### Post by sp40140 on 2014-06-28
I don't know if this thread is still open. I am appending my question:

I have same issue. about the Audio. no problem with Vid.
The issue is caused by a bug:[https://bugs.launchpad.net/ubuntu/+s...er/+bug/864735]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735")

now I am asking for help as well. As the workaround mentioned are not working for me.

currently I run 14.04 64bit with 3.11.0.20 kernel running on core2Quad  with 8 gigs ram and ATI HD7770 vid card. no luck with sound. in Audio  settings I only see analoge and Optical audio. Don't have option for  HDMI.

the only other option I can think of is to install latest kernel 13.15.2 and see if that works.
However, I have never upgraded a kernel manually. 
How risky is it?
What are the chances of new kernel resolving this missing hdmi audio issue?

Thanks,

---

### Post by QIII on 2014-06-28
Moved to its own thread from [http://ubuntuforums.org/showthread.php?t=2218045](http://ubuntuforums.org/showthread.php?t=2218045)

---

### Post by sp40140 on 2014-06-29
Upgrading to kernel 13.4 fixed the issue.

---

