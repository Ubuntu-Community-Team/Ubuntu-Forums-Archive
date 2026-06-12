---
title: "Hybrid Graphics + Splash Screen Display Issues"
date: 2011-04-06
forum: Multimedia Software
---

### Post by rjnole on 2011-04-06
I have an HP Envy 14 with "hybrid graphics", in this case an Intel integrated GPU and an ATI discrete GPU. I'm using Ubuntu 10.10 with kernel version 2.6.35-28 and have configured my system to use an encrypted LVM using the Alternate CD. The much-loved "vgaswitcheroo" module is enabled in my kernel and is working, as my Ubuntu installation works just fine once it has completed the boot process. Additionally, I'm able to create a script at the default run-level that turns off the inactive GPU to conserve power. What I'm *not* able to do consistently is enable the splash screen in which I'm prompted for the password for my encrypted root filesystem. Although I can click F3 and then enter the password via a text-based console, I'd like to be able to consistently see the splash screen as designed within the OS. It's like a car that you've restored; if it isn't working right, it'll bug you until you fix it. Well, this is bugging me. :(

I have followed the instructions here: [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics). My results are mixed; I find this workaround works OK about 10-20% of the time. As an aside, after a little playing around, I discovered that the script should be in /usr/share/initramfs-tools/scripts/local-top vs. /etc/initramfs-tools/scripts/local-top. In either case, the steps only work about 10-20% of the time. Moreover, putting the statements that manipulate the GPU's via /sys/kernel/debug/vgaswitcheroo/switch directly in the /usr/share/initramfs-tools/scripts/local-top/cryptroot script doesn't work either. (I know; probably not a great idea.)

What's the error message? 80-90% of the time is tells me that /sys/kernel/debug/vgaswitcheroo/switch can't be created and that it's an invalid path. I suspect that the scripts in "local-top" are getting executed too early & before the vgaswitcheroo module has created the "switch" file, as I know /sys is a virtual file system that's created each time the computer starts. But I don't know how to control the execution such that this issue doesn't occur.

If anyone has any tips or advice on how I might be able to solve this problem, I'd certainly appreciate the insight. Thanks!

---

