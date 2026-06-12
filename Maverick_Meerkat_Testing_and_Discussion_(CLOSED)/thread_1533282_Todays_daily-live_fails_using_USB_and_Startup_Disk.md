---
title: "Todays daily-live fails using USB and Startup Disk Creator -"
date: 2010-07-17
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by VMC on 2010-07-17
FYI, for those that use daily-live:
Todays daily-live [07/17/2010] fails using *Startup Disk Creator* on a usb hard drive. 

I get an error message:
 Syslinux - Unknown keyword in configuration file.

I found the error and once corrected it then works. Strange though how I can use the Startup Disk Creator on any previous iso and I don't have any issues.The problem is in the *syslinux.cfg* file:

# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo

Previous *syslinux.cfg* files:

include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo

The problem was in the *ui* reference. When I remove it then syslinux continued to boot.

Edit: After installing todays daily-live and using its *Startup Disk Creator* on a usb hard drive, everything worked including the "ui" reference. Not sure what happened, on the previous creations. Maybe an updated syslinux, maybe not. I use Lucid64 and Maverick64 dated 20100716 on the previous failed attempts.

---

### Post by cariboo on 2010-07-17
I just downloaded and am in the process of installing the netbook daily live cd, I used the startup disk creator to create a usb boot drive, except for a brain fart on my part, I haven't had a problem so far. :)

---

### Post by VMC on 2010-07-17
I found the problem, and it was an update to syslinux. That part is great news. Parted Magic iso couldn't be built on the older syslinux 3.63. Ubuntu now has updated it to 4.01. 

Using my Lucid64, which has syslinux3.63, it couldn't handle the "ui" reference, and the installed usb hd failed to boot.  Maverick's latest daily-live, has syslinux4.01, and it does work.

You can tell what version is being used by using this command:
```
head -n 9 /media/Boot/ldlinux.sys
```

Make sure you locate where your *ldlinux.sys* is located on your media.

---

### Post by cariboo on 2010-07-17
I used the netbook i386 daily live image from today, I didn't have to do anything special, I'm using the system to type this post after a successful installation.

---

### Post by ranch hand on 2010-07-17
I have an installation of Unity on this desktop with several other Desktop versions of 10.10 and I have noticed that the updates are really quite different.  UNE definitely updated that package before the Desktop got the update.  Do not remember if it was yesterday or the day before.  Got it this morning on the Desktop installs.

The kernels are 12 to 24 hours different too.  Kind of interesting.

---

### Post by stevetxt on 2010-07-18
I downloaded the daily iso today using a Karmic system and put it on a usb with startup disk creator.  It has worked on one system, an hp mini 110 netbook.  But my desktop would not recognize the usb as bootable, though there is no problem with an older bootable usb having karmic on it that was made in, uh, I forget, the release just before Karmic.  Not a problem since that system has a CD/DVD drive, but I think startup disk creator works for some systems and not others.

So far so good with meerkat on the netbook, though I had to change a driver to get wireless to activate.  Karmic was fun and pretty reliable, I skipped Lucid, and somehow got the itch for the new one - thanks to the tone of your discussions on here!

---

### Post by DevHead on 2010-07-29
Thanks for the great info in this thread. :D:D:D

---

### Post by Andrej_BB on 2010-08-06
Thanks for the infro from me too. Now it works great !

---

### Post by meborc on 2010-08-06
> **ranch hand said:**
> I have an installation of Unity on this desktop with several other Desktop versions of 10.10 and I have noticed that the updates are really quite different.  UNE definitely updated that package before the Desktop got the update.  Do not remember if it was yesterday or the day before.  Got it this morning on the Desktop installs.

The kernels are 12 to 24 hours different too.  Kind of interesting.

are you using the same apt sources file? sometimes the updates to local servers (like se.ubuntu.....) are behind the main servers a bit

---

### Post by ranch hand on 2010-08-06
I use the same server for all of the buggers except 2 that I use the Canadian one for just for comparison.

Unfortunately I have uninstalled UNE as it will not work for me anymore.  Just a white screen.  The CD will have some things on the desktop but it is not usable either as you can't read anything.  I will try it once a week to see if they have got it workable.

This is probably just due to my particular ATI card that is very poorly supported even by the driver listed for this card on the ATI site.  I was using the xorg.edgers drivers but they no longer do the trick.  I am sure it is just a matter of time.

---

### Post by keypox on 2010-08-10
Worked for me thanks. Remove ui from cfg file

---

### Post by Jakiejake on 2010-08-13
> **VMC said:**
> FYI, for those that use daily-live:
Todays daily-live [07/17/2010] fails using *Startup Disk Creator* on a usb hard drive. 

I get an error message:
 Syslinux - Unknown keyword in configuration file.

I found the error and once corrected it then works. Strange though how I can use the Startup Disk Creator on any previous iso and I don't have any issues.The problem is in the *syslinux.cfg* file:

# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo

Previous *syslinux.cfg* files:

include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo

The problem was in the *ui* reference. When I remove it then syslinux continued to boot.

Edit: After installing todays daily-live and using its *Startup Disk Creator* on a usb hard drive, everything worked including the "ui" reference. Not sure what happened, on the previous creations. Maybe an updated syslinux, maybe not. I use Lucid64 and Maverick64 dated 20100716 on the previous failed attempts.

Thanks Heaps!

---

### Post by psusi on 2010-08-20
So I just tried the daily build and ran into this then found this thread.  It has been 2 weeks and this critical bug has not yet been fixed?

---

### Post by ranch hand on 2010-08-20
It may not be getting a real high priority right now due to pushing to get bugs in the OS fixed.

The beta is due on 9-2 so the Beta RC ISO testing will be 8-29 or 30.

I would look for it to be fixed by then or earlier.

---

### Post by VMC on 2010-08-20
> **psusi said:**
> So I just tried the daily build and ran into this then found this thread.  It has been 2 weeks and this critical bug has not yet been fixed?
The problem is Lucid uses and older syslinux. There is a bug report on updating Syslinux to version 4, but for the life of me I can't find the bug report again. Its not as simple as one would expect.

Read this _[bug report]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/608382")_ regarding using disk-creator from Lucid. If you use Maverick to create a usb its works, of course.

---

### Post by psusi on 2010-08-20
Ohh, I see, so it is the startup disk creator in lucid that builds the config file and it is not compatible with the new version of syslinux in maverick.  Oh boy that is a difficult problem.

---

### Post by andrewabc on 2010-08-20
Yep, big problem and they better fix it before 10.10 final is released because everyone on 10.04 and older will have problems trying liveusb and we'll end up with a million threads about it.

---

### Post by tormod on 2010-08-20
> **psusi said:**
> Ohh, I see, so it is the startup disk creator in lucid that builds the config file and it is not compatible with the new version of syslinux in maverick.  Oh boy that is a difficult problem.
It is the other way around, right :) The config file is copied from the Maverick iso image, but the ldlinux.sys bootloader is installed using syslinux in Lucid, thus copied from the Lucid file system.

---

### Post by stone1343 on 2010-08-20
> **tormod said:**
> It is the other way around, right :) The config file is copied from the Maverick iso image, but the ldlinux.sys bootloader is installed using syslinux in Lucid, thus copied from the Lucid file system.

The good news is that it might not be that hard to fix, I think it's essentially just a text replacement (s/UI GFXBOOT/GFXBOOT/) if the syslinux version is < 4.

---

### Post by cariboo on 2010-08-20
I just installed from a usb device with today's daily live iso, so far except for not installing grub to the mbr of /dev/sda everything seems to be working OK. I didn't have to modify syslinux.cfg

---

### Post by tormod on 2010-08-20
> **cariboo907 said:**
> I just installed from a usb device with today's daily live iso, so far except for not installing grub to the mbr of /dev/sda everything seems to be working OK. I didn't have to modify syslinux.cfg
You probably prepared your USB device using Maverick (syslinux 4.x) then.

BTW, does anyone else experience kernel BUGs and stacktraces and udevd crapping out? I am just guessing it has to do with aufs. I have tried booting the isos directly with grub2 loopbacking as well as the "normal" way as laid out by USB creator. I have md5sum'ed the iso on the USB stick and I see this with two pretty different computers (both run 32bit, with Radeon cards).

---

### Post by andrewabc on 2010-08-20
> **tormod said:**
> You probably prepared your USB device using Maverick (syslinux 4.x) then.


Yep, a week or two ago I created liveusb in maverick of maverick and it worked fine. It is just older versions of ubuntu that don't work.

---

### Post by tormod on 2010-08-20
> **tormod said:**
> BTW, does anyone else experience kernel BUGs and stacktraces and udevd crapping out?
Looks like the famous [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/620810](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/620810) which should be fixed in next kernel build. I must have had bad luck trying out my first Maverick iso today...

---

### Post by susundberg on 2010-08-25
I tried this today with quite clean and up-to-date Lucid and it failed with the same error as above. The version of of syslinux seems to be 3.63:
sundberg@hopee:~$ head -n 9 /media/disk/ldlinux.sys

SYSLINUX 3.63 Debian-2008-07-15

Edit: removing the "ui" works also for me.

---

### Post by KdotJ on 2010-08-28
> **VMC said:**
> FYI, for those that use daily-live:
Todays daily-live [07/17/2010] fails using *Startup Disk Creator* on a usb hard drive. 

I get an error message:
 Syslinux - Unknown keyword in configuration file.

I found the error and once corrected it then works. Strange though how I can use the Startup Disk Creator on any previous iso and I don't have any issues.The problem is in the *syslinux.cfg* file:

# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo

Previous *syslinux.cfg* files:

include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo

The problem was in the *ui* reference. When I remove it then syslinux continued to boot.

Edit: After installing todays daily-live and using its *Startup Disk Creator* on a usb hard drive, everything worked including the "ui" reference. Not sure what happened, on the previous creations. Maybe an updated syslinux, maybe not. I use Lucid64 and Maverick64 dated 20100716 on the previous failed attempts.

Thank you x100000000
After hours of experimenting, this nailed it.

---

