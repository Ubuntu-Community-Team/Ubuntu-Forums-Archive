---
title: "Maverick won't boot from USB."
date: 2010-08-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by zob on 2010-08-06
I'm sorry if this is common knowledge. But I have downloaded latest alpha 3 release of ubuntu netbook and I can't run it from usb (havn't tried to burn it yet). I also tried with the earlier alpha 2.

I end up in busybox initramfs.
Last thing I see is something like "initialized i915..." and "No init found. Try passing init= bootarg"

That was on my eeepc 701. I've also tested it on my thinkpad t60 with similar results.

Is this just a known maverick alpha bug or should I prepare to report this?


I made the USB with unetbootin.

---

### Post by wilee-nilee on 2010-08-06
Mine boots fine using the ubuntu startup disc creator.

for a little while I had to edit the syslinux.cfg like in this link.
[http://ubuntuforums.org/showthread.php?t=1533282](http://ubuntuforums.org/showthread.php?t=1533282)

---

### Post by andrek on 2010-08-07
Common bug with unetbootin, try Ubuntu USB Startup Disc Creator.

---

### Post by bennachie on 2010-08-07
There could be something of a "gotcha" there if zob only has access to a netbook, with no external optical drive. I assume that  USB Startup Disk Creator on Lucid has now been updated so that it can deal with the latest version of Syslinux (it didn't work last week when I tried, and I've since replaced Lucid with Maverick in the course of ISO testing, so can't easily check). Even if my assumption is correct, you would still have to carry out a proper install and update of Lucid (no doubt from a USB stick), since the Lucid liveCD won't contain the correct version of Startup Disk Creator.

---

### Post by zob on 2010-08-07
Thank you, all three of you.
And bennachie you're spot on. I now found a bug repport and it seems to be excactly that problem. Incompatibility between syslinux 3.60 supplied by usb-creator (or unetbootin) on lucid and syslinux 4.01 in the ISO. Or something like that:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)

I havn't tried to remove the ui from syslinux.cfg as suggest in the bug-thread and also in the thread suggested by wilee-nilee. I'll be back when I know some more.

---

### Post by zob on 2010-08-07
That workaround - removing the ui for syslinux.cfg - seems to work for me. At least it is installing on my eeepc 701 in this very moment. Looking forward to seeing if unity can do something good for the 7" screen.

---

### Post by olivierz on 2010-09-21
I had the same problem with UNETbootin and also with Pendrive Linux. They did not work!!!!

Fortunately, if you do not have a nix machine at hand, there is still a solution:

[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

Lili USB: it installed my maverick netbook iso flawlessly, and the image booted perfectly.

I am now enjoying Unity on my eeePC 701 and my Aspire One

Try and see, you will also discover the brilliant features that are at hand, with a portable virtual box included in the installation.

I just love it now!!!

---

### Post by jvonmitchell on 2010-09-24
@bennachie
They haven't fixed the bug yet.  They have decided to fix the usb-creator though update-manager but haven't assigned the task to anyone yet.  It looks like it's been a month and a half since you wrote your comment so they are taking their time.  Maverick-beta is defiantly more like Maverick-alpha right now.  I noticed lynx was really buggy so I think the increased use of launchpad has bogged them down.

---

### Post by ranch hand on 2010-09-25
> **jvonmitchell said:**
> @bennachie
They haven't fixed the bug yet.  They have decided to fix the usb-creator though update-manager but haven't assigned the task to anyone yet.  It looks like it's been a month and a half since you wrote your comment so they are taking their time.  Maverick-beta is defiantly more like Maverick-alpha right now.  I noticed lynx was really buggy so I think the increased use of launchpad has bogged them down.
Do you really think the beta is being defiant or do you just spell like I do?   I like the concept though.

---

### Post by spikoley on 2010-10-04
> **andrek said:**
> Common bug with unetbootin, try Ubuntu USB Startup Disc Creator.

This worked for me.  Thanks!

---

