---
title: "945GME : Blank screen with 8.10"
date: 2009-01-16
forum: Multimedia Software
---

### Post by raghu1111 on 2009-01-16
I installed latest Ubuntu 8.10 on Eee Box which has Intel 945GME internal graphics controller.

The screen goes black randomly after a few minutes of use.. while browsing etc. Xorg.0.log has lines with "(EE) intel(0): underrun on pipe A!" in it. All the programs run normally. I can go to text login prompt with 'ctrl-alt-F1'. But coming back to X with 'ctrlk-alt-F7' shows the blank screen.

I can attach the full Xorg.0.log if interested. Is this a known problem? Is there any work around?

Where should I file a bug on this?

Thanks,
Raghu.

---

### Post by raghu1111 on 2009-01-16
Looks like this is a known issue : [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/311895](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/311895)

---

