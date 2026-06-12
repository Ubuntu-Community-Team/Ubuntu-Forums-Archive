---
title: "Login loop, reason full hard disk"
date: 2022-10-22
forum: MINT
---

### Post by thisisnicole on 2022-10-22
Hey there,

my hard drive is full and now I'm in a login loop (and eyerolling about my lazy past self but anyway... :KS). I know my password is right. My Linux knowledge is very rudimentary but I already tried some tips.

I'm using Mint 20 Cinnamon on Lenovo L490

This is what I already tried: 

- Logging into the Shell - this doesn't work, neither with the Ctrl + Alt+F3 combination nor with any other F-key 

- Pressing Esc when booting the laptop, using the advanced options and then trying everything possible in recovery mode (cleaning off some space, repair, update grub ...)

- Installing Linux again which I then realized didn't make any sense because I need a file which is on the laptop and not on my last backup ,_.

Any help is appreciated, thank you so much in advance!

Cheers
N.


[SIZE=1][IMG]https://emojipedia-us.s3.dualstack.us-west-1.amazonaws.com/thumbs/120/emojipedia/294/melting-face_1fae0.png[/IMG][/SIZE]

---

### Post by jeremy31 on 2022-10-22
Moved to Mint subforum

---

### Post by yancek on 2022-10-23
What exact message do you get?  Use the Mint or any live usb/dvd to access the installed system and start by deleting files you don't need.  I would start by deleting files in /var/log as that is where files get very large.  Is it the / (root filesystem) that is full or another partition (separate /home)?  Do you have Mint installed on a single partition?

---

### Post by thisisnicole on 2022-10-24
> **yancek said:**
> What exact message do you get?  Use the Mint or any live usb/dvd to access the installed system and start by deleting files you don't need.

This helped, thank you so much! I wasn't able to delete anything but I copied the files and am now rewriting the hard disk :) Thank you so much!

---

### Post by TheFu on 2022-10-24
Your post is exactly why many people don't use the default disk layout that the installer creates.  If you setup separate partitions or volumes for /var, /home, /, /boot and for swap, you can probably avoid this issue in the future.

A full file system is really bad on any Unix system, but especially bad if /var is shared with other parts of the OS.  Don't let that happen and setup log file limitations so they never get larger than you can handle.

---

### Post by yancek on 2022-10-24
>  I wasn't able to delete anything

You need root permissions to delete directories/files in /var.  Are you familiar with using sudo?

---

### Post by TheFu on 2022-10-24
> **yancek said:**
> You need root permissions to delete directories/files in /var.  Are you familiar with using sudo?

Unix systems use the same file permissions model. It is elegant, but something new for MS-Windows people. It needs to be learned to avoid hours, days, weeks, months, years of frustration with any Unix-like OS.  It is simple, but does take about 45 minutes to learn the basics. I don't know of any shorcuts to this knowledge, I'm sorry to say.

---

### Post by Skaperen on 2022-10-24
i agree.  learning the file system concepts is essential for every Unix(-like) system/platform.  just learn it and you'll be grad you did.

---

