---
title: "DVD tray won't stay open w/ MythTV .22"
date: 2009-09-26
forum: Mythbuntu
---

### Post by slamhound on 2009-09-26
I have a strange problem that only seems to occur with MythTV .22 (Mythbuntu or not).  I have tried this on three different computers with different hardware, so it is not a problem with my drive.  On the various computers, I have tried at least one of the following options (sometimes more than one on the same computer):

Installed Mythbuntu 9.04 and then upgraded to MythTV .22 with Avenard's repositories.
Started with Ubuntu 9.04 and then installed MythTV .22 from Avenard's repositories directly (i.e., no upgrade from .21).
Installed Mythbuntu 9.10 alpha 6

In each case, after MythTV runs, the DVD drive becomes unusable, closing too quickly to put anything in or take anything out.  I can sometimes put a disc in, but when I eject it to take it out, the tray extends fully and then immediately retracts.  After this, it will extend about an inch and then retract, and I can't fix it until I reboot.  For the system that loads Myth automatically, sometimes the problem never gets solved and I have to open the drive during boot to get access.  For the system where MythTV doesn't load automatically, the drive functions normally until I use Myth, after which I have this problem. 

The problem never occurred when I was using 9.04 or 8.10.

Searching the forums comes up with an error from 8.10 (not specific to myth), but that seems to have been quickly fixed (I see no references to it in Jaunty).  It is also a little different because it only occurred when a disc was in the drive (on one box I can't even get the drive open to get a disk in).  

Any thoughts on how to fix this?

---

### Post by SpareTimeGizmos on 2009-09-26
FWIW, I have the same issue. I found a thread about a similar bug in udev (sounds like you found the same thing too) that was fixed a long time ago. Don't know if this is an old bug that's come back or something new.

---

### Post by slamhound on 2009-09-29
Well, for others who have this problem, I found no perfect solution, but I can get access to my DVDs.  Here's what I do:

After playing a DVD in myth, I select "eject media" from myth.  It opens the tray fully and then it quickly closes (too fast to get the DVD out).  If I hit the physical eject button as soon as it closes, it will open again and stay open.  However, then I can't close it again.  Pushing on it or pressing the physical eject button does nothing.  But then if I wait about 10 seconds, the tray closes automatically and the DVD is usable.

Still looking for a better fix (and am open to suggestions), but that works for now.

---

### Post by superm1 on 2009-09-30
I think this is caused by mtd running as a daemon in the background.  Not sure yet why, but killing mtd appears to help.  If anyone wants to help look through mythplugins/mtd code, most appreciated :)

---

### Post by Steve Goodey on 2009-09-30
Yup, from a terminal killall mtd sorts it.

Now the problem is a proper fix?

Steve.

---

### Post by superm1 on 2009-09-30
Builds after 22128 should have it fixed:

[http://svn.mythtv.org/trac/ticket/7212#comment:2](http://svn.mythtv.org/trac/ticket/7212#comment:2)

---

### Post by Steve Goodey on 2009-09-30
Excellent!

I loved the comment on the trac:-

"Here at MythTV, we recognize that your DVR shearing off your wife's fingers is the kind of thing that will get you in trouble."

You guys are great.

Steve.

---

