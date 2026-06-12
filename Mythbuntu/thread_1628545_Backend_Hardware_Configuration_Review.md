---
title: "Backend Hardware Configuration Review"
date: 2010-11-22
forum: Mythbuntu
---

### Post by JWB47 on 2010-11-22
Currently, I have a combined FE/BE on an ASRock Nettop ION 330 recording OTA through 2 HVR-950Q tuners. I have an external 1TB drive for storage of recordings. I am running on Mythbuntu 10.04 LTS and MythTV 0.23.1+fixes26863.

This is working very well, but has some difficulty with multiple recordings and simultaneous commercial flagging.

My plan is to create a standalone backend with 4 tuners and an initial 2TB storage feeding eventually 3-4 separate Frontends.

Until next August when Digital conversion takes place in Canada, all OTA broadcasts except one that I wish to receive are Digital. Therefore, I have a short-term need to receive analog UHF until then as well as recording from old VHS tapes

Below is the proposed configuration for the backend. I would appreciate any suggestions to improve the configuration. Besides the role described above, I am looking for a reliable system that will last for many years.

This configuration is based on the Intel High-End ATX system from the AVS Forum "Guide to Building a HD HTPC" 
-- [http://www.avsforum.com/avs-vb/showthread.php?p=18816470](http://www.avsforum.com/avs-vb/showthread.php?p=18816470).

I realize it may be overkill in some areas. In particular, the Graphics Card is much more than what is needed for a backend,  but as there is no internal graphics on the motherboard, I needed something. Suggestions are welcome here.

===============================================================
Category          Description of Product
----------           ----------------------
CPU                 Core i5-760 2.8GHz LGA1156
CPU Cooler       Cooler Master Hyper 212 Plus 4 Heat Pipes, Copper Base 
                       (RR-B10-212P-GP)
Motherboard     GIGABYTE GA-P55A-UD4P LGA1156 Intel P55 chipset ATX
Memory           G.SKILL F3-12800CL9D-4GBNQ DDR3-1600 2 x 2GB Kit
Graphics Card  EVGA - GeForce GTS 250 1GB (01G-P3-1145-TR)
HDD OS           WD Cavier Black (WD6402AAEX) 640GB SATA3 7200RPM 64MB Cache
HDD Data         WD Cavier Green 2X1tb (WD10EARS) 1000GB (1TB) SATA 3 Gb/s                                64MB Cache
Optical BD        LG UH10LS20K Black 10x Blu-ray Read 16x DVD+/-R/RW Write SATA
PSU                 Corsair TX650W CMPSU-650TX 650W
Case                LIAN-LI PC-8N
===============================================================

Thanks in advance for any assistance you can give.

John

---

### Post by ian dobson on 2010-11-23
Hi,

The system looks OK. I have a "big" backend server Quad Core Intel 2.83GHZ/8Gb ram that has 2 DVB-C tuners and 2 ip tuners and a 6Tb RAID 5 array (4x2Tb wd green drives). With this system I can record 4HD streams and 2SD streams and watch a SD stream on a remote frontend which commflagging 3 streams at the same time before it runs out of steam.

Having 8Gb ram makes a big difference when recording as the system can cache more data before needing to write to the disk, but 4Gb should be more than enough.

With regards to the graphic card, use the cheapest/passive cooled card you can find. I have a 128Mb NVidia 7300 in the backend (which I never use-The box doesn't even have a monitor attached).

You know that the ears drives are 4K sector drives and you need to manually partition them so the partition starts on a 4K boundry to get the maximum performance.

Regards
Ian Dobson

---

### Post by JWB47 on 2010-11-23
Ian:

Thank for the Feedback.

I had wondered about memory, so will look into increasing to 8MB. I will also look at  a lower spec graphic card.  I agree once it is setup, I will seldom attach a monitor.

Thanks again.

John

---

### Post by LowSky on 2010-11-23
Backend wont really need a massive video card, unless you plan to use it for something. I'm using a Nvidia 460GTX only because my system is a frontend/backend. It gets a lot of use for gaming and video watching.

4GB of RAM is fine, going to 8GB is not required for normal setup. Ian Dobson's setup is something dreams are made of. My system handles 5 recordings, commercial flagging, and watching video at the same time with only 4GB of RAM, and a quadcore processor.

Get 2TB drives. They cost not much more than 1TB drives. And recordings take up a great deal of space.

---

### Post by ian dobson on 2010-11-23
> **LowSky said:**
> Backend wont really need a massive video card, unless you plan to use it for something. I'm using a Nvidia 460GTX only because my system is a frontend/backend. It gets a lot of use for gaming and video watching.

4GB of RAM is fine, going to 8GB is not required for normal setup. Ian Dobson's setup is something dreams are made of. My system handles 5 recordings, commercial flagging, and watching video at the same time with only 4GB of RAM, and a quadcore processor.

Get 2TB drives. They cost not much more than 1TB drives. And recordings take up a great deal of space.

Hi,

Not really I'm already planning the next upgrade/split. I currently Have 7 2tb drives in my backend (4 in a RAID5 array and 3 in a RAID0 array for backups). The RAID0 array is on a 5 port port multplier card so only uses 1 port on the motherboard. My current plans are to upgrade the backup system to
1) 3x 3Tb drives
2) Upgrade main array to 5x 2Tb
Split he network into 2 segments (Normal PC use and Multimedia), shift the backend into the celler where noise isn't a problem.

Regards
Ian Dobson

---

### Post by JWB47 on 2010-11-23
> **LowSky said:**
> Backend wont really need a massive video card, unless you plan to use it for something. I'm using a Nvidia 460GTX only because my system is a frontend/backend. It gets a lot of use for gaming and video watching.

4GB of RAM is fine, going to 8GB is not required for normal setup. Ian Dobson's setup is something dreams are made of. My system handles 5 recordings, commercial flagging, and watching video at the same time with only 4GB of RAM, and a quadcore processor.

Get 2TB drives. They cost not much more than 1TB drives. And recordings take up a great deal of space.
LowSky:

I agree about not needing a "massive" Video card and will look for an alternate that fits with the rest of the build. So far for passive ones, the cost is about the same as the GTS 250. The server will be located in the basement server room, so there is the future possibility of driving a  display in the Family  Room. I am easy here so it may come down to  what is easily available locally.

I am trying to "future-proof" this build as much as possible, so I will compare the price difference between the 4 and 8 GB RAM before deciding.

My current 1TB drive only has 58GB left, so  I am aware of the space recordings take up. I have  already done several clean-ups to recover space on this drive. I will take this into consideration. Currently, it is about $30 extra per drive for the 2TB models.

Thanks for the feedback.

John

---

