---
title: "DVD Drive/Media Problems - Drive seems to disappear"
date: 2010-05-20
forum: Multimedia Software
---

### Post by anothernewuser on 2010-05-20
Been wrestling with media and ubuntu for a while now .... 

Suppose I'm gonna try to pick off the problems one by one.

To quickly summarize ... when my system restarts it *seems* completely normal.  If there's a disk in the DVD drive (either CD or DVD) its automatically detected and will play normally ... for a while.  Eventually ... sometimes as a result of launching other applications ... sometimes when the CD/DVD is the only thing going ... sometimes when the machine is just sitting there doing nothing ... always when it goes to sleep ...it just stops and then its like the drive isn't there.   Can't play CDs or DVDs cause ... well ... the machine thinks the drive ain't there basically.

Kind of keeping a running diary here ([http://ubuntuforums.org/showthread.php?t=1484579](http://ubuntuforums.org/showthread.php?t=1484579)) ... I suppose that's bad form .. but its working for me.

I've enabled the Medibuntu repositories ... downloaded all the right files (I assume) ... poked around in a few things here and there ... nothing seems to work permanently.   A reboot makes the system *seem* perfect again and then eventually it isn't regardless of what is running or not running really.

The last couple of days when ubuntu starts there's a string or repeated errors just before the login screen which appear in the dmseg and messages logfile (I assume it's the same message though it flashes by too fast during boot to be 100% sure):


In Messages these appear ... repeatedly dozens of times perhaps more:
VFS: busy inodes on changed media or resized disk sr0

***Google turned up this explanation for the above error "you get this message when you eject a CD that is not unmounted. Check mount" ... whatever that means :) ***


and:
[   20.442319] sr 3:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
 [   20.442341] sr 3:0:1:0: [sr0] Sense Key : Illegal Request [current] 
 [   20.442363] sr 3:0:1:0: [sr0] Add. Sense: Illegal mode for this track
 [   20.442407] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00

Similar messages appear in Dmseg ... the sector number varies but the form of the message doesn't.

As this is occurring before login I wouldn't mind fixing it it there's a way. These messages haven't been there since I upgraded from 8.04 only the last couple of days but I can't say that I can link their appearance to any one thing I tried in fixing this problem.

This is all way over my head ... any advice would be greatly appreciated :)




Well ...one of the commands I ran in trying to fix all this up was:

sudo chmod 660 /dev/sr0; chgrp cdrom /dev/sr0

changing it to:

sudo chmod 660 /dev/sr0; sudo chgrp cdrom /dev/sr0 

seems to have cleared up the string of error messages before boot if nothing else.

Now I suppose I can go back to trying to figure out why the dvd playback stops and the system stops recognizing the existence of the drive ... which .. it just did.


Okie dokie ... after 2 restarts the string of error messages during boot before login is gone.

I wonder if the rest of my troubles are some other seemingly harmless command I ran trying to get a perfect system.

---

