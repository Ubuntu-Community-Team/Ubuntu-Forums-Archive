---
title: "Trouble With Screen Brightness on Acer Aspire 5733z"
date: 2014-01-21
forum: Multimedia Software
---

### Post by grungedaze on 2014-01-21
Hello, everyone!

I've been having some trouble with my Acer Aspire 5733z recognizing my Intel HD graphics driver. 
I've not been able to adjust my brightness prior to installing Ubuntu. I've tried a few different versions, just to make sure that the trouble I was having wasn't just with a particular version of Ubuntu. So far, I've installed Ubuntu, 12.04, 13.04 and 13.10 with absolutely no avail. I've been to the Intel for Linux Graphics page and have installed these packages each time I have tried to install a new version of Ubuntu. I've tried nearly everything I've read in the forums so far and it's not been of much help regarding the issue I've been having. :confused: Any help would be very greatly appreciated and welcomed!

Here are the specs, if this is any help.


[LIST]
[*] Processor Intel Pentium P6200 / 2.13 GHz ( Dual-Core ) 
[*] RAM installed size 4.0 GB 
[*] Hard Drive 500.0 GB - Serial ATA-300 
[*] Operating System Microsoft Windows 7 Home Premium 64-bit Edition 
[*] Display Type 15.6 in TFT active matrix 
[*] Max Resolution 1366 x 768 ( HD ) 
[*] Graphics Processor Intel HD Graphics Dynamic Video Memory Technology 5.0 
[*] Optical Drive DVD±RW (±R DL) / DVD-RAM 
[/LIST]

---

### Post by Toz on 2014-01-21
Hello and welcome to the forums.

Which version of Ubuntu do you have installed now?

Can you open a terminal window, type or copy/paste the following commands, and post back the resutls:
1. Info about your kernel boot parameters:
```
cat /proc/cmdline
```
2. Confirm your video card and driver:
```
lspci -k | grep -A2 VGA
```
3. Info about your recognized backlight interfaces:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

We should be able to get something to work for you.

---

### Post by grungedaze on 2014-01-21
Hello, and thank you for your response. :D

Currently, I have version 13.04 running on my system.

This is what I got back after typing those down:

> BOOT_IMAGE=/boot/vmlinuz-3.8.0-35-generic root=UUID=336cf20c-b79a-41c8-9426-fa4018b5fdc4 ro quiet splash vt.handoff=7

> 00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) 
Subsystem: Acer Incorporated [ALI] Device 0601
Kernel driver in use: i915

> /sys/class/backlight/acpi_video0/brightness
9
9
/sys/class/backlight/intel_backlight/brightness
976
976

---

### Post by Toz on 2014-01-21
Try using the **acpi_backlight=vendor** kernel parameter. To test it, follow the "Temporarily Add a Kernel Boot Parameter for Testing" instructions in the [Kernel Boot Parameters wiki]("https://wiki.ubuntu.com/Kernel/KernelBootParameters"). If anything goes wrong, simply restart the computer to get it back to where it is now. If it works, we'll make it permanent.

---

### Post by grungedaze on 2014-01-21
I don't believe it! This actually worked! :)
Words cannot express how grateful I am for this, thank you!
I have been looking for a solution for this problem for so long!
A million thanks :)

---

### Post by Toz on 2014-01-21
Glad to hear it worked. Did you follow the instructions on the same page to make it permanent?

---

### Post by grungedaze on 2014-02-15
I didn't catch this, sorry. I did make it permanent. Thank you for all the help. :-D

---

