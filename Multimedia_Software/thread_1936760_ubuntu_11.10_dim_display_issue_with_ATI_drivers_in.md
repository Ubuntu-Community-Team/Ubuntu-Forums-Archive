---
title: "ubuntu 11.10 dim display issue with ATI drivers installed"
date: 2012-03-06
forum: Multimedia Software
---

### Post by Imagery on 2012-03-06
Hi everyone,

I've posted this question everywhere so far and have looked everywhere for any help or info on this issue.  I just installed the ATI drivers for my laptop and it all works fine, but I'm getting that infamous dim display issue at login. And it is not saving my brightness settings.

I tried the brightness  fix:  

echo 10 > /sys/class/backlight/acpi_video0/brightness

But this fails and I do get a GTK error when trying to save the rc.local changes:

(gedit:3801): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

Here's my lspci | grep VGA listing:

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M]

Anyone have any idea how I can fix this issue?

---

