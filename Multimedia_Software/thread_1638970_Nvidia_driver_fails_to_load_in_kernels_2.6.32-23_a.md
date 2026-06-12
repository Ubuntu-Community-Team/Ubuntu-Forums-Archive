---
title: "Nvidia driver fails to load in kernels 2.6.32-23 and later (raid possibly related)"
date: 2010-12-06
forum: Multimedia Software
---

### Post by DarkReverend on 2010-12-06
I've been using kubuntu for a while, and I've been having this issue since the release of the 2.6.32-23 kernel.  Originally, I thought it was related to my raid array and this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/601740](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/601740)  I'm still not convinced they're not related, but there is also apparently the possiblity of an nvidia driver issue.  

Previously, I rebooted infrequently, and I had a spare hard drive installed, so my grub menu would always appear (as it detected an alternate OS on this drive) and it was trivial to select the 2.6.32-22 kernel.  Since I installed all updates, including the -35 kernel, it ran update-grub and now I have to press shift when I reboot.

Specs/Summary:
Kubuntu 10.04
amd64.
nvidia driver 195.36.24
RAID 1 (linux software raid)

kernels installed: 2.6.32-21 - 2.6.32.25

when I boot with -22 or earlier, everything works great.  when I boot with -23 or later, I get the kubuntu splash screen, followed by it switching to tty2, then I get it switched back to where the X screen should be, with the system log displayed, and then it switches back to tty2.  After installing -35, I panicked a bit as I'd never had the grub screen not show (not knowing about the shift key), and so I poked around logs and it showed nvidia driver errors.  I tried removing my xorg.conf file and rebooted, and I got the desktop to show again.  I prefer the nvidia driver as I sometimes use dual monitors.

Has anyone else hit this issue, and is there any known solution?

---

### Post by sydbat on 2010-12-06
> **DarkReverend said:**
> I've been using kubuntu for a while, and I've been having this issue since the release of the 2.6.32-23 kernel.  Originally, I thought it was related to my raid array and this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/601740](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/601740)  I'm still not convinced they're not related, but there is also apparently the possiblity of an nvidia driver issue.  

Previously, I rebooted infrequently, and I had a spare hard drive installed, so my grub menu would always appear (as it detected an alternate OS on this drive) and it was trivial to select the 2.6.32-22 kernel.  Since I installed all updates, including the -35 kernel, it ran update-grub and now I have to press shift when I reboot.

Specs/Summary:
Kubuntu 10.04
amd64.
nvidia driver 195.36.24
RAID 1 (linux software raid)

kernels installed: 2.6.32-21 - 2.6.32.25

when I boot with -22 or earlier, everything works great.  when I boot with -23 or later, I get the kubuntu splash screen, followed by it switching to tty2, then I get it switched back to where the X screen should be, with the system log displayed, and then it switches back to tty2.  After installing -35, I panicked a bit as I'd never had the grub screen not show (not knowing about the shift key), and so I poked around logs and it showed nvidia driver errors.  **I tried removing my xorg.conf file and rebooted, and I got the desktop to show again.**  I prefer the nvidia driver as I sometimes use dual monitors.

Has anyone else hit this issue, and is there any known solution?I have not had this problem (I also do not use RAID). However, the part I highlighted seems to have solved things for you? Perhaps it is an xorg configuration problem, not a kernel or RAID problem.

That said, when you removed xorg.conf and got your desktop back, is it still running the latest NVidia driver? If so, then you should be fine. Just go into the NVidia settings and make sure they are what you want and save to xorg.conf. If that creates the problem again, try not saving to xorg.conf. I think the NVidia settings dialogue auto-saves elsewhere, and saving to xorg.conf might not be needed.

---

### Post by DarkReverend on 2010-12-06
> **sydbat said:**
> That said, when you removed xorg.conf and got your desktop back, is it still running the latest NVidia driver?


Sorry, left out this detail.  When I remove xorg.conf, it's not using the nvidia driver, it's using the open source one.  I also tried re-running nvidia-xconfig to regenerate xorg.conf (only one of my monitors is plugged into the computer right now), and when I rebooted, I had the same issue, so if it is the xorg.conf, it's the default generated one too.

---

### Post by sydbat on 2010-12-06
> **DarkReverend said:**
> Sorry, left out this detail.  When I remove xorg.conf, it's not using the nvidia driver, it's using the open source one.  I also tried re-running nvidia-xconfig to regenerate xorg.conf (only one of my monitors is plugged into the computer right now), and when I rebooted, I had the same issue, so if it is the xorg.conf, it's the default generated one too.Have you tried reinstalling the NVidia driver? Might work.

---

### Post by DarkReverend on 2010-12-06
> **sydbat said:**
> Have you tried reinstalling the NVidia driver? Might work.

I can't try this out until I get home tonight.  in the meantime, any other ideas?

---

### Post by shreepads on 2010-12-06
Please have a look at the manual at:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

**_Extract:_**

> 
**[SIZE="4"]Kernel and Mesa Updates[/SIZE]**

Every time a new kernel comes out you will probably have to manually rebuild the NVIDIA binary driver kernel module. This can be done by booting to the new kernel and then running:

```
sudo sh NVIDIA* -K
```

on the previously downloaded NVIDIA installer file.

---

### Post by DarkReverend on 2010-12-08
I tried reinstalling it, no such luck.  as for shreepads suggestion, that URL has the following warning on it: This is not the recommended way to install the NVIDIA drivers - please see BinaryDriverHowto/Nvidia for the supported method.  

this isn't how I installed the driver the first time, I just used the package repository as shown in the recommeded link.

I do have my monitor plugged in via DVI, but it's a desktop.  I'm going to try the Xorg Fix it recommends tonight, but I welcome any further input.

---

### Post by DarkReverend on 2010-12-10
Solved!

The above didn't work, but here's what happened.

I went through the log files again, and carefully looked for error messages, and it ultimately looked like the nvidia kernel module was not built for the new kernel.  reinstalling the nvidia package confirmed this, as I got the following message:

> Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.

I found this: [http://typethinker.blogspot.com/2010/02/ubuntu-fails-to-load-nvidia-kernel.html]("http://typethinker.blogspot.com/2010/02/ubuntu-fails-to-load-nvidia-kernel.html") which gave me correction steps.  I did one thing differently, (removed and reinstalled rather than reconfigured) so I'll explain it that way.  I'll summarize them below in case the blog changes its URL, but all hat tips to the original author.

1) download the headers for your kernel version (ex: sudo apt-get install linux-headers-2.6.##-##-generic)
2) download the nvidia src (I think this is necessary, not sure) ex, sudo apt-get install nvidia-185-kernel-source
3) run sudo apt-get remove nvidia-current
4) run sudo apt-get install nvidia-current
5) run sudo nvidia-xconfig in case you need to regenerate the xorg.conf

---

