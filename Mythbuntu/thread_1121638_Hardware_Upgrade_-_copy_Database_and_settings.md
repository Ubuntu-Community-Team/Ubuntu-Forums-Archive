---
title: "Hardware Upgrade - copy Database and settings"
date: 2009-04-10
forum: Mythbuntu
---

### Post by mr. 100prozent on 2009-04-10
Hello everybody, i am running mythbuntu since a couple of month. I made some software upgrades and i think i am running 9.04 alpha something. 
My config is:
Server: 
AMD Athlon 64 3000+ (1800MHz)
Mainboard: MSI K8T Neo2
1GB Ram
One Harddisk for System (i think about 20Gb)
LVM with currently 2 x 1TB for videos and stuff
Hauppauge PVR150 TV Card
3Com NIC

Frontend:
AMD Sempron 3000+
Mainboard: Asusu A7NBX-E
1,25GB Ram
One Harddisk for System
Connects to Server and gets all the Data (including TV) from there

My Question:
I made a hardware upgrade, i use now:
Mythbuntu 9.04 beta
AMD Athlon 64x2 5600+
4GB Ram (~3,2GB usable)
One Harddisk for System (6GB)

I want to use the same Harddisks as i used in my old Server (2 x 1TB) configured as LVM in my new server. All mountpoints should be the same, also the tv card is the same. Is it possible to copy the database with all the settings (Font size in mythtv, covers from the dvds, tv channels,..) to my new server and if yes which files do i have to copy?

---

### Post by klc5555 on 2009-04-10
> **mr. 100prozent said:**
> Hello everybody, i am running mythbuntu since a couple of month. I made some software upgrades and i think i am running 9.04 alpha something. 
My config is:
Server: 
AMD Athlon 64 3000+ (1800MHz)
Mainboard: MSI K8T Neo2
1GB Ram
One Harddisk for System (i think about 20Gb)
LVM with currently 2 x 1TB for videos and stuff
Hauppauge PVR150 TV Card
3Com NIC

Frontend:
AMD Sempron 3000+
Mainboard: Asusu A7NBX-E
1,25GB Ram
One Harddisk for System
Connects to Server and gets all the Data (including TV) from there

My Question:
I made a hardware upgrade, i use now:
Mythbuntu 9.04 beta
AMD Athlon 64x2 5600+
4GB Ram (~3,2GB usable)
One Harddisk for System (6GB)

I want to use the same Harddisks as i used in my old Server (2 x 1TB) configured as LVM in my new server. All mountpoints should be the same, also the tv card is the same. Is it possible to copy the database with all the settings (Font size in mythtv, covers from the dvds, tv channels,..) to my new server and if yes which files do i have to copy?

It sounds like an ordinary database backup and restore from backup should do the job simply enough. Basically as described here: [http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance)
It's just that you're going to restore the database file onto the new machine instead of onto the original machine.

The password for backing up will be whatever the mysql password is on the old machine; the password for restoring will be whatever the mysql password is on the new machine; and there is no space between -p and the actual password.

---

### Post by mr. 100prozent on 2009-04-10
Thanks very much, thats what i searched for.
Btw, how can i see which version of mythbuntu is running?

---

