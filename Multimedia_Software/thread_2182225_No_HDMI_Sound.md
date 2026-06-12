---
title: "No HDMI Sound"
date: 2013-10-20
forum: Multimedia Software
---

### Post by talisman.26 on 2013-10-20
I've checked some other posts, but can't seem to find a solution for my problem.  I'm running dual boot OS, Ubuntu/Win 7.  HDMI video works, but no sound in Ubuntu,  HDMI video and sound both work with Win 7.  I've looked at Alsa, and tried switching drivers, but it didn't do seem to do anything at all.  

Alsa info: [http://www.alsa-project.org/db/?f=ba475fe59e8cf37c1198e55e1722be2ab77eaad4](http://www.alsa-project.org/db/?f=ba475fe59e8cf37c1198e55e1722be2ab77eaad4)

From lspci:

00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6290]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler HDMI Audio

Any help you can give is appreciated.

---

### Post by Yellow Pasque on 2013-10-20
Try workaround 1 here: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735)

Also, while you're making that change, it may be a good time to add radeon.dpm as well: [https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later](https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later)

---

