---
title: "Can't boot Ubuntu 11.04 A3"
date: 2011-03-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by VMC on 2011-03-09
If you tried todays, mar9, livecd and tried to install, and got the partman-141 error.

here is the [bug report]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/730209") to add or "me-too" it.

Edit: Fails again using todays, [COLOR=Red]**March 10th**[/COLOR], daily-live ISO:

"natty-desktop-amd64.iso 10-Mar-2011 08:19 680M"

---

### Post by West201 on 2011-03-14
I have the same problem :(. I just installed an hour ago, and now I've been searching the internet like crazy trying to find a solution.. To make that worse my wife is upset cuz all her files can't be accessed

---

### Post by bcbc on 2011-03-14
It's fixed apparently - just download the new wubi.exe from the bug report linked to above.

Don't know why this would affect you accessing your files though!?

---

### Post by MadCow108 on 2011-03-14
> **jessejj89 said:**
> I have the same problem :(. I just installed an hour ago, and now I've been searching the internet like crazy trying to find a solution.. To make that worse my wife is upset cuz all her files can't be accessed

don't use alpha software when you need a working system ...

you should be able to access the data with a live cd/usb of an older ubuntu version.

---

### Post by bcbc on 2011-03-14
This bug does not result in loss of data. It just stops a fresh wubi install from booting - windows is unaffected.

If however you had a previous wubi install it would have removed it (standard wubi behaviour). In that case, the virtual disk is deleted and - unless you had a backup - the data on it is gone.

+1 to not using alpha software though - that's always good advice.

---

### Post by VMC on 2011-03-14
It appears there's a fix on the way. Hopefully by tomorrow. According to the latest post#17 of the [bug report]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/730209").
From reading other earlier reports it didn't look like it would be fixed until beta release.

---

### Post by corrytonapple on 2011-03-14
I downloaded the latest alpha today for some testing, and went to go install in Virtualbox with a Windows 7 host.  I went through, and when I got to the "Do you want to include the latest updates and install these extras, I hit forward.  All it does is seem to load with the spinning cursor and all, but nothing changes.  Any help?:)

---

### Post by GeoPirate on 2011-03-15
This is why I always have a separate stable partition and a testing one.

---

### Post by alessio80 on 2011-03-15
Same problem, nothing to do.
Usb install on my asus 1005ha too
Can anyone help us?

---

### Post by t1497f35 on 2011-03-15
Hi folks,
for like a week all daily builds of amd64 fail to install yielding some "ubi-partman" related error. Anyone knows if it's being taken care of at all?

In case it matters my hw is listed in attachment.

---

### Post by ikt on 2011-03-15
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by mc4man on 2011-03-15
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/730209](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/730209)

Till fixed the alternate installer works, the actual Alpha 3 iso works and while a pita you can use a current daily live to install if you boot to the live cd, enable all the sources, downgrade several of the ubiquity packages to a working version,  ect. ect

---

### Post by t1497f35 on 2011-03-15
> **mc4man said:**
> [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/730209](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/730209)

Till fixed the alternate installer works, the actual Alpha 3 iso works and while a pita you can use a current daily live to install if you boot to the live cd, enable all the sources, downgrade several of the ubiquity packages to a working version,  ect. ect
Thanks a lot

---

### Post by VMC on 2011-03-15
> **t1497f35 said:**
> Hi folks,
for like a week all daily builds of amd64 fail to install yielding some "ubi-partman" related error. Anyone knows if it's being taken care of at all?

In case it matters my hw is listed in attachment.

Use the search button. [Here is related info with the bug report link]("http://ubuntuforums.org/showthread.php?t=1703911").

---

### Post by cecilpierce on 2011-03-15
Not solved for me yet, just tried to install daily-live an hour ago and the same thing... locked up again:sad:

---

### Post by cariboo on 2011-03-15
There are several threads already about this problem.

---

### Post by cecilpierce on 2011-03-15
> **cariboo907 said:**
> There are several threads already about this problem.

The ubi-partman error thread is marked SOLVED but I just tried it a couple hours ago and still no go, I was trying the 32 bit version though.

---

### Post by t1497f35 on 2011-03-15
> **cecilpierce said:**
> Not solved for me yet, just tried to install daily-live an hour ago and the same thing... locked up again:sad:
The fix might be committed but it might not yet be part of the new isos, imo you should try the isos of the next 1-2 days or so.

---

### Post by cecilpierce on 2011-03-15
> **t1497f35 said:**
> The fix might be committed but it might not yet be part of the new isos, imo you should try the isos of the next 1-2 days or so.

I took a chance this morning, I figured it was too early to try but dumb me ! Takes over an hour with my slooooow internet :P

---

### Post by MadCow108 on 2011-03-15
> **cecilpierce said:**
> I took a chance this morning, I figured it was too early to try but dumb me ! Takes over an hour with my slooooow internet :P

use zsync to only download the updated parts
there are many howtos on this forum

---

### Post by cecilpierce on 2011-03-15
> **MadCow108 said:**
> use zsync to only download the updated parts
there are many howtos on this forum

Thanks, I'll give that a try tomorrow.

---

### Post by corrytonapple on 2011-03-15
> **cariboo907 said:**
> There are several threads already about this problem.
Each situation seems to be different.  Like we go from 64-bit to 32-bit, and some with boot problems to others with install problems.  
Fortunately, I do have an idea of what I need to do.  Thanks for the bug report!  I will use the alternative installer.

---

