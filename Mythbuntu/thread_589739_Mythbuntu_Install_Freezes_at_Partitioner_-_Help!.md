---
title: "Mythbuntu Install Freezes at Partitioner - Help!"
date: 2007-10-24
forum: Mythbuntu
---

### Post by snwbrder0721 on 2007-10-24
I'm doing a clean install of mythbuntu on my dell (733mhz, 386mb ram, nvidia geforce 5500, hauppauge pvr-350) and the live CD boots ok, then when I click the icon to install mythbuntu the installer starts and gets through to the partition step and freezes at 46% "checking hard disks" while trying to set up the partitioner. It seems to be doing something for about 2 minutes then the mouse and keyboard lock up, forcing me to hit the restart button on the machine. I've tried it 4 times with identical results. I did the CD verify and the data is OK. My hard drive is an older WD, 20gb (I plan to add a larger drive later). It is formatted and completely blank (it's formatted in fat32 right now). I also tried it with xubuntu already loaded on it with the same results. Anyone had a similar experience or can offer some help on what I can do to solve this? 

I'm new to linux so detailed explanations are appreciated. Thanks!

---

### Post by davemorris on 2007-10-24
I've had problems with installers before where the cdrom has been dodgy and it'll always fail at the same point.  Are you able to try a different cdrom drive to eliminate this?

---

### Post by jord1242 on 2007-11-03
bump. Same issue as I am having, and I can't figure out how to resolve this. Any ideas?

---

### Post by de3pc77 on 2007-11-03
I am new to Linux and Mythbuntu, but I had similar issues last week during my first install. 

I had multiple hard drives (a SCSI and a SATA) connected and had to disconnect the SATA to get it to install.  It would freeze at the partitioning.  Once I only had one drive connected it installed ok.  

Then I reconnected my SATA and wanted to reformat it to EXT3 (it was NTFS) but nothing would work (i tried GParted).  I used KillDisk to blank the drive and then I was able to use GParted to partition my second drive ok. Like I said, this is new to me, so maybe I did something else inadvertently that solved the issues, but that is my experience so far. 

Not a typical guru answer, but I hope this helps

---

### Post by jord1242 on 2007-11-03
That actually makes some sense, because my slave never recognized for 7.04 and I never took the time to look into it. I will try disconnecting the slave and see what happens.

Thanks for the quick response!

JJ

---

### Post by jord1242 on 2007-11-03
Well I gave that a try and disconnected my slave, then disconnected my master (reconnecting the slave) and it locked up at 46% done during the partition phase of the install both times. 

I would guess maybe it was the CD-ROM drive, but taht is a new drive I just put in a few days ago and it worked just fine under 7.04.

JJ

---

### Post by jord1242 on 2007-11-03
That seems to have been the problem. It has gotten by that point (although I gave up on MythBuntu and I am just using Kubuntu). 

I am going to try and get the slave going again after the install with your directions. I'll let you know.

Thanks again for the help!

JJ

---

