---
title: "Will old /var/lib/mythtv/recordings be deleted during upgrade?"
date: 2010-11-13
forum: Mythbuntu
---

### Post by marek_online on 2010-11-13
So I'm looking to upgrade from my old 8.04, 0.21 MythTV setup to a 10.10, 0.23 one. I've backed up my database, and I have the following partitions:

First hard drive (320GB):
ext3 /boot
ext3 /
ext3 /home
xfs /var/lib/mythtv/recordings

Second hard drive (160GB)
/var/lib/mythtv/store (for music, photos, videos etc.)

I had thought that putting things on separate partitions would allow me to keep the data across a new installation. However, when I go to start the installation, after manually setting the partition table, it warns me that I have mount points for /var - but all system directories, including /var, will be deleted during the installation process.

Will all sub-directories go too? Have I wasted my time with the separate partitions?

---

### Post by ian dobson on 2010-11-13
Hi,

How are you trying to upgrade (Boot from CD or implace update through the package manager)?

I've upgraded my backend several times and have my recordings in /data/mythtv on my raid5 array, and have never seen a message about partitioning during the update.

I usually update from the terminal using:-
```

Network upgrade for Ubuntu servers (Recommended)
1.Install update-manager-core if it is not already installed:   

sudo apt-get install update-manager-core 2.edit /etc/update-manager/release-upgrades and set Prompt=normal  

3.Launch the upgrade tool:   

sudo do-release-upgrade4.Follow the on-screen instructions.   

Other upgrade options exist, please view the Upgrade Notes to learn more.
```

From this link:- [http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

Regards
Ian Dobson

---

### Post by marek_online on 2010-11-13
> **ian dobson said:**
> 
How are you trying to upgrade (Boot from CD or implace update through the package manager)?


A fresh install from CD, rather than updating though the package manager.

> **ian dobson said:**
> 
I've upgraded my backend several times and have my recordings in /data/mythtv on my raid5 array, and have never seen a message about partitioning during the update.


Yeah, I wouldn't expect that to be a problem. I might case, because the system I'm updating is so old, I figured updating rather than reinstalling would be the bigger hassle.

I think I'm just going to do the labour-intensive version and backup all of my /var/lib/mythtv/recordings folder onto an external hard drive, and copy it all back over after the upgrade.

Cheers.

---

### Post by ian dobson on 2010-11-13
Hi,

Don't forget to backup your mythtv database.

Why not do a full backup then try a inplace upgrade. My backend started as a 7.10 box and I've updated it all the way to 10.10 without any major problems.

Regards
Ian Dobson

---

