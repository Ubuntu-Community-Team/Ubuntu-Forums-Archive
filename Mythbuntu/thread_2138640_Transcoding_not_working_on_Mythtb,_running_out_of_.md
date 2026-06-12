---
title: "Transcoding not working on Mythtb, running out of space fast"
date: 2013-04-24
forum: Mythbuntu
---

### Post by grunge09 on 2013-04-24
I have a mythtv on Ubuntu 11.04 backend,and mythtv data is on another pc with 4x2tb raid5. That is already up to 2.8tb.   I have checked my logs and the transcoder does not work.  Is there any way to save space on the files and still be able to view the files in mythtv like I currently am doing?

1st PC - Mythtv Backend & Frontend

MSI MB - gigabit NIC
AMD 965 3.4GHz quad core CPU
4 GB RAM
1TB Sata II HD
DVD Rom Drive
Geforce 210 PCI Express video card with HDMI Out to 37" LCD TV)
Ubuntu 11.10 Desktop with Mythtv installed
HVR-2250 (using analong duners only)
2 x PVR-500 cards using each 2 tuners
(that makes 6 analog tuners)

Mythtv data os on my Ubuntu Server PC

2nd PC - Ubuntu Server (using Samba for 3 other machines also for backups)

Asus MB - gigabit NIC
AMD 6000+ dual core CPU
2 GB RAM
ATI mach 64 pci video card
1 8GB Flash Boot Drive
4 2tb drives in RAID5 with new in the box spare USING MDADM and onboard sata controllers.
using Webmin, recently grow the raid cause I was running out of space.  And in like a weeks time with all that I am recording I used up 400 GB.

---

### Post by klc5555 on 2013-04-24
Obviously you have two choices. 1) Debug your transcoder isssues, or 2) buy more storage.

I'd recommend 2) until you sort out your transcoder issues. Storage is cheap nowadays.

---

### Post by grunge09 on 2013-04-25
A recent "grow" of my raid5 array took 20 hours.  Plus the Fsck.ext4 & the resize2fs took about 1 hour.  

Seems like it would be easier to fix the transcode issues.

So how do I debug my transcoder issues?

---

### Post by klc5555 on 2013-04-25
Logically, you'd start from the logs which you said you checked when confirming that your transcoder does not work to see what's going wrong.  If you've been trying to use the included transcoder to save space, you've presumably set it up in the frontend for MPEG-4 (or RTjpeg), since the hardware encoders are not supposed to work, according to [http://www.mythtv.org/wiki/Removing_Commercials](http://www.mythtv.org/wiki/Removing_Commercials)

---

