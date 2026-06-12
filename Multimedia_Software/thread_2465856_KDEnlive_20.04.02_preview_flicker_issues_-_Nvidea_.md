---
title: "KDEnlive 20.04.02 preview flicker issues - Nvidea 340 drivers?"
date: 2021-08-13
forum: Multimedia Software
---

### Post by steve234 on 2021-08-13
Hi all,

I come to you having had no response for a month or so to this issue on the [r/kdenlive subreddit]("https://www.reddit.com/r/kdenlive/comments/od6yw0/flickering_in_monitor_windows_but_not_in_logging/"). 

Essentially the preview window is totally unusable using either the latest PPA or appimage versions. See the above post on reddit - including an OBS screen capture of the issue. 

My system is an older i7-based box with 16bb ram and a basic Nvidea card. I'm running Lubuntu 20.04 LTS.

I'm hoping it's not a Nvidia driver issue, as I need the proprietary drivers for cloud-based CAD (WebGL). I've been using other editors (Shotcut mostly) as a workaround, but now want to consider KDEnlive again, as it may run on all my machines (whereas Shotcut may not).

Any help debugging would be appreciated.

---

### Post by Autodave on 2021-08-14
Laptop or desktop?  What nVidia card?  Where are you getting your nVidia drivers from?

---

### Post by steve234 on 2021-08-14
Thanks for the reply. I can answer some of that but need to do further testing:

- Desktop;
- GeForce G210
- 340 Drivers installed via apt. No ppa that I was aware of (it was a very fresh install)

Further testing required as:

- KDEnlive was dead weight, so I removed it
- I then had the issue listed here 
[https://ubuntuforums.org/showthread.php?t=2465592](https://ubuntuforums.org/showthread.php?t=2465592)
- The resolution of the above was installing legacy drivers listed in a bug report from the kelebek333 nvidea legacy ppa.

I therefore need to re-install KDEnlive and get back to you after a test with the kelebek333 drivers

---

### Post by steve234 on 2021-08-14
Just reinstalled and tested - exact same issue

---

