---
title: "Best way to set up RAID 5"
date: 2009-01-18
forum: Mythbuntu
---

### Post by scottac on 2009-01-18
I am building a front/backend and need to know the best way to set up RAID 5. I am using an ASUS P5N7A-VM motherboard which has support for raid 5. however I know a lot of people use software raid within linux to set up their arrays. 

What is my best option here.  keep in mind that I am new to linux and have never dealt with a RAID array in linux or mythbuntu before.

Thanks for any help..

Fredo

---

### Post by albinootje on 2009-01-18
> **scottac said:**
> I am building a front/backend and need to know the best way to set up RAID 5. I am using an ASUS P5N7A-VM motherboard which has support for raid 5. however I know a lot of people use software raid within linux to set up their arrays. 


You should first find out whether you mobo has real hardware RAID or fakeRAID :
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by bah1976 on 2009-01-20
If we assume it's a fakeraid, and not a real hardware raid, then you want to go with a software raid config.  I used these links to get mine setup.  I have a single boot drive, and all data / media is on a 3-disk raid-5 array formatted XFS.  No LVM for me, as i don't need it since RAID can expand in this version.

[http://www.gagme.com/greg/linux/raid-lvm.php]("http://www.gagme.com/greg/linux/raid-lvm.php")

[http://mythtv.org/wiki/index.php/LVM_on_RAID]("http://mythtv.org/wiki/index.php/LVM_on_RAID")

---

