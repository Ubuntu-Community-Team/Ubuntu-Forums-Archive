---
title: "/dev/dvd and dev/sr0 Acidrip"
date: 2010-04-21
forum: Multimedia Software
---

### Post by xtremedementor on 2010-04-21
Hi,

I am trying to use acidrip to rip some dvds.

DVDs play fine in Mplayer and k9copy detects the dvds as /dev/sr0

In disk utility the dvd drive shows as /dev/sr0/ and mount point as /media/cdrom0/

AcidRip looks for /dev/dvd/ and cant find the DVD drive with an error message "Can't read DVD Track" if i change this to /media/cdrom0 acidrip trys to load but says "no valid files found"

I was looking at this last night and i believe it has something to do with (Please feel free to correct my terminology as i am a nOOb) the following

/dev/sr0/ being the device and /media/cdrom0 being the mount point
AcidRip is looking for a mount point(?) of /dev/dvd/.
I also believe this needs to be set up as a dynamic link?

I am just looking for 
a)some clarification on if what i have said is correct?
b)wether this will solve my problem
c)if so how to set up the dynamic link between /dev/sr0 and /dev/dvd

Thanks in advance for any help as always.

Ubuntu 9.1

---

### Post by xtremedementor on 2010-05-02
Solved here

[http://ubuntuforums.org/showthread.php?t=1459526](http://ubuntuforums.org/showthread.php?t=1459526)

---

