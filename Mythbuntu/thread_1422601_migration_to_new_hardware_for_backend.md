---
title: "migration to new hardware for backend"
date: 2010-03-05
forum: Mythbuntu
---

### Post by aovermy on 2010-03-05
My backend is great, since replacing its power supply it's been rock stable. However, it's also dated. It's a single core 32 bit Athlon XP (thoroughbreed) 2000Mhz CPU. The capture hardware is a USB plextor go7007 MP4 adapter (captures Svideo from dish STB), a USB fusion hdtv usb ATSC adapter and 2 PCI ATSC adapters. It's got an FX5200 nvidia card because I use frontends to actually watch TV. 

Really, for what I'm doing and even planning to do, the CPU is good enough for most purposes. By moving to a new system, I'm getting PCIE (the current board is AGP), 6 onboard SATA (I have 6 SATA drives right now with a 4 SATA port PCI adapter) and that's 3.0 Gbps SATA (as opposed to the 1.5Gpbs I'm limited to right now).

So I have a X3 AMD 64 bit CPU system in test right now to replace my existing backend. It will have a Fusion HDTV 7 dual digital PCIE tuner, the usb fusion hdtv adapter in the current system, a PCI based ATSC tuner and a HDPVR to replace the go7007 adapter (instead of capturing from svideo of dish STB it will capture component from dish STB). All the SATA harddrives will move into the new backend, the OS drive will not. 

Right now the new backend is in test, so I'm proving out its drivers and such. It has mythbackend running on it and has the tuners defined. It has its own OS drive so I won't be moving that from old to new. I'm doing all this with my downstairs dish receiver and a set top antenna circa 1960 (metal loop and rabbit ears). 

Before doing the cutover, I will rename the hostname to match what the old system is called. There's a file under /etc that defines that, IIRC.

So my question is, right now I'm planning to wait for a period when nothing is being recorded, take a DB backup of the old system and put it somewhere it can be copied to the new system; power down the old unit (but keeping it nearby); power on the new one; hook up the HDPVR to the dish STB (but not unhook the go7007 yet) via component and optical; disconnect my 3rd tuner card from the old system from antenna and hook the dual fusion card up to the antenna. Then copy the database backup and restore it to the new system. Then remove all tuner cards and define the new ones. I won't need to add new sources, because they're already in there. I will need to set up input sources to capture cards. Then make sure all tuners are working by doing manual records on them. 

If that goes OK, then change over the fusion usb tuner and one of the PCI tuners (doing a powerdown for that). 

If all goes well, the new system is now ready. Otherwise, I disconnect the new one and fallback to the old one. 

I'm hoping to be done in under 2 hours, but it's hard to say. 

Has anyone done something like this? What unexpected things did you run into?

---

### Post by ian dobson on 2010-03-05
Hi,

The plan sounds OK. 

1) I've replaced several server systems in my time and one thing I've learnt is change the IP address of the old server before powering it off for the last time. If you still need to get some information from the old system you can power it up and telnet in to the new IP address.

2) You might need to play with the storage groups if you're copying your recordings from the old to the new system and be carefull with the permissions.

3) It might be better to export the mysql database then import it into the new system rather than trying to just copy the sql database.

Always allow abit longer than you think you'll need to transfer a system, 2 hours isn't that long, and it's better to "go slow and do it right" rather than quick and dirty.

Regards
Ian Dobson

---

### Post by aovermy on 2010-03-05
Thanks, you  make some good points and made me realize one more thing.

I need to copy the fstab from old system to new system. I'm using blkids in there, so it shouldn't matter in which order I plug the SATAs. 

I am using a storage group that spans 2 hard drives, but as long as my fstab is good, it should restore OK.

I use dhcp for ip address though, so either I'm going to have to change my router to assign the old one's ip @ to the new one, or set the new one statically, or change the screen in mythtv setup to just use the new @ after I restore the database.

The other thing I realized...since both systems have their own OS disk, I can actually keep the old one powered up while I work on the new one after transferring the video disks. That means I'll be able to sftp over anything needed by the new system.

---

### Post by aovermy on 2010-03-07
Well it's over. The migration is finished with not too many headaches.

---

