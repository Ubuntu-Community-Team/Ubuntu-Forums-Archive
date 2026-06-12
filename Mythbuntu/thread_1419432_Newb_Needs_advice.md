---
title: "Newb Needs advice"
date: 2010-03-01
forum: Mythbuntu
---

### Post by PopaTim on 2010-03-01
I am converting a retired pc into a mythbuntu box. I plan on using dual 2Tb hard drives in a raid 1 (software) configuration. I need these to be access from windows pc as a media repository/fileserver with a seperate partition for windows backups from 3 pc's. Other wise the wife just needs simple VCR capability for her soaps and 'the Bachelor".  

With the 2TB drives, are there any known issues? I plan on dedicating 1 to 1.5TB for media andrthe remaining on backup space. Wife is about 3 months backlogged on her soaps...LOL

How should I partition and format the drives? I believe I read that I should use gpart instead of fdisk on drives this size. What format should the partitions use or does samba negate that issue? I do wih to be able to access media as well as backups from the windows pc's


Any thoughts on setting up the raid 1? I plan on mirroring the swap file too. Basically If 1 drive should fail the other should work perfect as a standalone. I did find a few threads on setting up the raid but nothing really about setting it up after Mythbunu was installed.
Heres is the one I was using as a guide as it seems to be the most recent updated. If anyone has a better guide I would love to see it.
[https://help.ubuntu.com/community/Installation/RAID1%2BLVM](https://help.ubuntu.com/community/Installation/RAID1%2BLVM)
(note the use of fdisk instead of gpart...)

The two 2TB drives have not been ordered yet; planning on samsung fe3's as the WD green drives are not raid compatible. 

BTW - I am new to linux> I have only been reading up on it a few days since finding Mythbuntu as an option to media center and thought I'd try it out. The system is setup with dual 320Gb drive currently and I have successfully installed Mythbuntu but not gotten the drives into a mirror yet.

AMD64 3400+
1Gb Corsair Cas 2 ddr
ATI x1650 512Mb AGP graphics
two Samsung sata 320Gb hdd's


Thank you,
Tim

---

### Post by blackoper on 2010-03-03
If it was me I'd just get another 2tb drive and set it up as a raid5. This would provide the 1 disk loss tolerance and give you 4TB usuable. Or if 2tb is your target you could get three 1tb drives at $70 each and come out cheaper than the two 2tb disks (again mdadm raid5).

There was a recent discussion of hard drives on the mythtv users mailing list. No consesus was met on the best drives but generally most were staying away from WD and seagates. The most happy users had hitachi's and samsungs.

The windows file shareing can be done easily with samba/cifs. I prefer setting up webmin gui program and using it to set up all my shares and for simple monitoring.

The ati card *might* be an issue. Try it and find out. I personally only use nvidia cards for my display systems. On servers I've used ati, intel, via graphics.

---

