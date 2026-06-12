---
title: "Unable to Install Multi-Disc Game"
date: 2010-04-22
forum: Multimedia Software
---

### Post by X-Malleus on 2010-04-22
I came across an interesting problem.  I'm trying to install The Sims 2 (which I'm aware currently does not run properly in wine anyway), using the multi-CD version.  The installation goes normally, up until it comes time to switch from disc 1 to disc 2.  The installer prompts me to insert disc 2, but it seems that Ubuntu still believes that the installer doesn't want me to open the drive, because, when I try to open it, it doesn't open, and a window pops up with the following message:

Unable to eject CD-RW/DVD±RW Drive
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

Anyone know if there's anything I can do about this?

---

### Post by 762sks on 2010-04-22
i had a similar problem. i was using ubuntu 9.10 i think. which ever the current version is. anyways i was trying to install x plane 9 and i had to unmount the drive and then remount it with the other disk. a friend told me that the beta doesnt have this issue. hope this helps

---

### Post by mc4man on 2010-04-22
there are 2 fairly straightforward ways - 
open a terminal and go 
```
wine eject
```
or do like in windows ( this method allows the eject button to work, maintains proper path for subsequent disk(s)

find the name of the install/setup file and the wine drive letter for the drive the disk is in.

Ex - Setup.exe in drive D
```
wine D:/Setup.exe
```

---

### Post by X-Malleus on 2010-04-23
> **mc4man said:**
> there are 2 fairly straightforward ways - 
open a terminal and go 
```
wine eject
```or do like in windows ( this method allows the eject button to work, maintains proper path for subsequent disk(s)

find the name of the install/setup file and the wine drive letter for the drive the disk is in.

Ex - Setup.exe in drive D
```
wine D:/Setup.exe
```

Thanks so much!  wine eject worked perfectly.

---

