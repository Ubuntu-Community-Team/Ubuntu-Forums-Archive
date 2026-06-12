---
title: "Dual Boot with XP and fakeraid."
date: 2009-01-20
forum: Mythbuntu
---

### Post by philman on 2009-01-20
I'm new to this so please bare with me.  I currently have XP installed on an 80Gb drive and have 3 750Gb drives assembled in Raid 5 using the mb's fakeraid.  Everything's running fine under XP.  Using GParted, I partioned the 80Gb drive into two 40Gb partions, one for XP using NTFS and the other ext3 with the intent of installing Mythbuntu.  I ran through the installation using the alternate CD, saying that I wanted to activate the raid devices.  The installation dectected that I had XP installed and I selected the option to choose which OS to boot.  Seems like it should work.  But the first time I tried this it booted straight to XP...no option to select which OS to boot to.  The second time I ran through the installation (after reformatting), I couldn't boot to either.  Any ideas as to what I'm doing wrong?  The intent was to use the raid array for media storage (Myth backend) so Myth will need to see it but I also need XP for some work related stuff (only occasionly).  I'm a total newbie when it comes to Linux so any help would be greatly appreciated!

Mb: ECS GF8200A
CPU: AMD 5000+
HDDs: WD 80Gb x 1  Samsung 750Gb x 3

---

### Post by DocNaq on 2009-01-28
I am also interested in this thread.  I currently have Ubuntu 8.10 installed on a RAID 5 using Ubuntu's software raid.  I've done some research and I don't think Windows can see Ubuntu's software RAIDs. 

I would like to setup a fakeraid like you have yours. 1 HDD for the OSes and the other 3 in a RAID 5 for storage. Would it be easier to install Windows first and then Ubuntu from Windows? Did you ever solve your booting issue?

---

