---
title: "Ubuntu 14.04 brightness keys do not work on Dell N411Z"
date: 2014-06-03
forum: Multimedia Software
---

### Post by madvinegar on 2014-06-03
Hi to all. I really need your help and expertize to try to find a solution to the problem I describe in the title of this post.
I own a Dell n411z laptop. I have installed in the past ubuntu 12.04, 12.10, 13.04. In all these releases the brightness keys worked out of the box without me having to add any grub parameter or create any conf file inside xorg.conf.d

As of ubuntu 13.10 and 14.04 the brightness keys (Fn+F4 and Fn+F5) are completely dead. They do not produce any results in xev, or acpi_listen or evdev.
I have tried all the parameters i can think of in grub and I have also created the 20-intel.conf file inside xorg.conf.d but I have not managed to solve the matter.
acpi_backlight=vendor, acpi_osi=Linux, acpi_osi=\"!Windows 2012\" etc etc etc. Maybe the syntax is wrong? Or do I need to use a combination of parameters? I really don't know.

It is really disappointing and frustrating as the keys work fine up to ubuntu 13.04. 
All the rest of the function keys (wifi, volume, keyboard brightness etc) work just fine.
I also upgraded my BIOS to A06 (A06 being the last recomended and available BIOS for my N411z according to DELL), but again it did not solve the matter.

For your information I can adjust the brightness just fine either via terminal or via the brigthness bar in system settings > brigthness. But the function keys are just dead.

I have also participated in a launchpad bug but no solution yet: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1229591](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1229591)
Tried later kernels (3.14 and 3.15) but still no solution.

Below you can find some terminal results that might help you produce any ideas or suggestions.


[http://paste.ubuntu.com/7582689/](http://paste.ubuntu.com/7582689/)

```
mike@Linux-Dell:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.13.0-27-generic root=UUID=849fb8e5-8216-4cec-a2d2-4d0ce8a2130d ro quiet splash vt.handoff=7

```

```
mike@Linux-Dell:~$ lspci -nnk | grep -iA3 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
    Subsystem: Dell Device [1028:051b]
    Kernel driver in use: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)

```

```
mike@Linux-Dell:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
16
16
16
/sys/class/backlight/intel_backlight
4845
4845
4882

```

Finally just to add that the brightness adjustment via the function keys works just fine when I am in BIOS or even in the Grub menu. So the function keys stop working after loading the OS (!)

Your kind assistance would really be very much appreciated.
Any ideas and/or suggestions are more than welcomed.

---

