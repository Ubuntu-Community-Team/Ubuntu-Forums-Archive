---
title: "Tuner config file location"
date: 2009-12-18
forum: Mythbuntu
---

### Post by Zeedok on 2009-12-18
I am running Mythbuntu 9.04 on my HTPC.  Here are my specs:

```
Antec Micro Fusion 350 HTPC Case
Intel Core 2 Duo E8400 CPU 3.0 GHz
Gigabyte GA-EG41M-S2H Mainboard
4GB DDR2 PC6400 (2x2GB) Dual Channel RAM
8X Dual Layer DVD+RW + 20X DVD+-RW + CD-RW Combo Drive
1TB 7200RPM SATA HDD
512MB NVIDIA Geforce 8400GS
Gigabit Ethernet
Hauppauge Nova-T-500 MCE Dual DVBT SD/HD tuner
```

When Karmic was released, I tried a clean install and had problems with my tuner set-up (see [here]("http://ubuntuforums.org/showthread.php?t=1299986") for the details).  Essentially, my tuners were not locking onto signals properly, even with the onboard amplifier turned on.  I tried testing the cards and firmware in a number of ways and in frustration reinstalled 9.04.

It has been a couple of months now and I am starting to contemplate another attempt to upgrade to Karmic.  I have backed up my home directory as a precaution, but I would like to know where the tuner setup configs, channel listing etc are on 9.04, so that I can ensure these are backed up.

Can anyone offer some advice?

---

### Post by nickrout on 2009-12-18
in thedatabase

why not do an upgrade, then the db settins will still be there and no need to rescan.

---

### Post by Zeedok on 2009-12-18
> **nickrout said:**
> in thedatabase

why not do an upgrade, then the db settins will still be there and no need to rescan.

This is my intention (I only did a clean install before because I stuffed a few things up), but I want to cover myself in case things don't go to plan - my wife will kill me if I spend ages trying to fix another install.

Is the database is my home directory or is it in a system directory(ie would I have already backed it up)?

EDIT: Sorry, found [this page]("http://www.mythbuntu.org/Upgrading") on backing up the database

---

### Post by Zeedok on 2009-12-18
OK, so I have successfully backed up my database.  Can someone confirm for me that this will contain my channel tuning data and my tuner card settings?

Thanks

---

### Post by nickrout on 2009-12-19
Thats what I said wasn't it?

---

### Post by ian dobson on 2009-12-19
Hi,

All the settings/channel information/recorded program information is stored in the mysql database.

Regards
Ian Dobson

---

### Post by Zeedok on 2009-12-19
I have backed up my database, upgraded my system, corrupted my database, deleted the database, created a new database and restored mybackup!!!

I have a few Karmic kinks to iron out, but essentially I have come out the other side!!

---

