---
title: "Black Screen on boot after upgrading to 11.04"
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jakewc2 on 2011-04-14
Hi, I upgraded from 10.10 to 11.04 a couple of days ago, and after grub it goes straight to black screen. I am running a Aspire5736Z,Intel Pentium T4500, Intel GMA 4500M card x64 bit machine. Had no problems with Ubuntu 10.10, worked perfectly. I notice quite a few other people have similar problems, but no resolution yet. Has anybody been able to ete this fixed?

---

### Post by dino99 on 2011-04-14
to let you know about errors while booting, remove "splash" from boot line (can be permanent tweaking /etc/default/grub, then sudo update-grub)

---

### Post by jakewc2 on 2011-04-15
Are you talking about going into grub, then pressing e and removing splash from there.....already tried that. If it will give some errors, how do I get those back to show you.

---

### Post by Duncan Williams on 2011-04-15
had similar problems awhile back > nvidia video card drivers.

---

### Post by jakewc2 on 2011-04-15
Ah, mine isnt an nvidia, its a Intel GMA. How did you get around it?

---

### Post by jakewc2 on 2011-04-15
I cant even get into recovery mode, because exactly the same thing happens, the screen goes black.  even tried fresh install over the top using live cd, and even that caused the screen to go black. I think something is turning off the backlight, as soon as you try to boot into the Natty.

---

### Post by Kevbert on 2011-04-15
Had that problem with an Nvidia card and recovery mode did not work. Just re-installed 11.04 daily build today without any extras and now everything seems to be working (haven't tried compiz yet !)

---

### Post by Duncan Williams on 2011-04-15
I was getting into a gui using recovery > failsafe graphics for this session.
Then recent updates fixed video drivers.

---

### Post by jakewc2 on 2011-04-15
ok, how did you install the daily build? I now have three partitions, I want to get rid of the Ubuntu 11.04 partition, and try again, but I dont know how to do that.

---

### Post by tormod on 2011-04-15
"Black screen" can unfortunately mean many things. Is the backlight turned off? You should be able to determine this by looking at the screen in a dark room. Can you switch to a console with ctrl-alt-F1? Can you log into it from another machine? Would be nice to get the output from the "dmesg" command.

You should be able to block the intel KMS driver by booting with "i915.broken=1" as a kernel option. The unrecognized "broken" module option will keep the module from loading, and X will fall back to the vesa driver. Then you can access the kernel messages in /var/log/kern.log*.

If it is not the backlight, the more general question would be, is the screen black because there is something wrong in X or KMS while there really is something on the screen, or is the boot process stuck at a point where the screen should be painted black?

More tricks here: [https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

---

### Post by Kevbert on 2011-04-15
> **jakewc2 said:**
> ok, how did you install the daily build? I now have three partitions, I want to get rid of the Ubuntu 11.04 partition, and try again, but I dont know how to do that.

You can get the Daily Build from [[COLOR="Red"]here.[/COLOR]]("http://cdimage.ubuntu.com/daily-live/current/") When you select the partition to install to, just, use the one that you currently have 11.04 on - I believe the option is 'Something else' and mount it / Also make sure you select and tick the format box.

---

### Post by jakewc2 on 2011-04-16
> **tormod said:**
> "Black screen" can unfortunately mean many things. Is the backlight turned off? You should be able to determine this by looking at the screen in a dark room. Can you switch to a console with ctrl-alt-F1? Can you log into it from another machine? Would be nice to get the output from the "dmesg" command.

You should be able to block the intel KMS driver by booting with "i915.broken=1" as a kernel option. The unrecognized "broken" module option will keep the module from loading, and X will fall back to the vesa driver. Then you can access the kernel messages in /var/log/kern.log*.

If it is not the backlight, the more general question would be, is the screen black because there is something wrong in X or KMS while there really is something on the screen, or is the boot process stuck at a point where the screen should be painted black?

More tricks here: [https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)


Hi, well, I had to install Maverick back, and deleted the Natty installation. I could just see the sign in screen at the back ground, but the screen was black, I could hit Fn+F6 and the screen back light would flash on for a second, then turn off again. I didnt try logging in from another machine. I am writing from the machine using Maverick reinstall, and backlight works perfectly. I could enter via an older kernel, and it would show Natty, but it wasnt the right kernel. Even trying to install via a live cd, as soon as the screen for the installation started, it went back. Its Natty side, not Acer side. 

As far as the other stuff you mentioned, I am lost, I dont understand what you were trying to tell me. I do learn quickly though.

---

### Post by tormod on 2011-04-16
To debug this (so that you hopefully one day can run Natty and later versions) please install the latest natty kernel onto your maverick system. Get the linux-image-2.6.38-8-generic_2.6.38-8.42_i386.deb from [https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux) and install it (it will also keep the old maverick kernel, no worries). Then select the new kernel at boot, and after you get the dark screen you can restart with ctrl-alt-F1 ctrl-alt-del. Now choose the old maverick kernel again (2.6.35). Go through /var/log/kern.log* and find the corresponding log (search for 2.6.38 in it) and attach this log to your bug report. Create the bug report with "ubuntu-bug xserver-xorg-video-intel". TIA.

PS. You can afterwards remove the new kernel package, or edit /etc/default/grub to choose the maverick one by default (GRUB_DEFAULT=2).

---

### Post by dankoleary on 2011-04-16
> **Duncan Williams said:**
> I was getting into a gui using recovery > failsafe graphics for this session.
Then recent updates fixed video drivers.
Thanks! This worked for me

---

### Post by jakewc2 on 2011-04-28
> **tormod said:**
> To debug this (so that you hopefully one day can run Natty and later versions) please install the latest natty kernel onto your maverick system. Get the linux-image-2.6.38-8-generic_2.6.38-8.42_i386.deb from [https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux) and install it (it will also keep the old maverick kernel, no worries). Then select the new kernel at boot, and after you get the dark screen you can restart with ctrl-alt-F1 ctrl-alt-del. Now choose the old maverick kernel again (2.6.35). Go through /var/log/kern.log* and find the corresponding log (search for 2.6.38 in it) and attach this log to your bug report. Create the bug report with "ubuntu-bug xserver-xorg-video-intel". TIA.

PS. You can afterwards remove the new kernel package, or edit /etc/default/grub to choose the maverick one by default (GRUB_DEFAULT=2).


Hi, well, I was just wondering, I am not sure I understand much of what you said there, would need somebody to explain it a bit more, and go through it with me. Its release day, and even with a bug report I still havent been told if its fixed yet, anybody know if the backlight is fixed or not? 

I tried looking for the image, on that page, but couldnt find it. Looks like I wont be able to upgrade today.

---

### Post by tormod on 2011-04-28
> **jakewc2 said:**
> Hi, well, I was just wondering, I am not sure I understand much of what you said there, would need somebody to explain it a bit more, and go through it with me. Its release day, and even with a bug report I still havent been told if its fixed yet, anybody know if the backlight is fixed or not?

Where is the bug report?
> I tried looking for the image, on that page, but couldnt find it. Looks like I wont be able to upgrade today.
On the web page, click on the little arrow/triangle next to "2.6.38-8.42" then you get the list of .deb packages.

From there on, if you have problems, tell us what you tried and what exactly failed or what you did not understand.

---

