---
title: "NWZ-S618F does not mount"
date: 2008-10-24
forum: Multimedia Software
---

### Post by Canellas on 2008-10-24
Hi,

I am using 8.04, and when I plug my Sony NWZ-S618F, it shows on Nautilus (2.22.5.1), after I click 'Computer', an icon with the lable 'USB Disk'. 

When I double click on it, it says "Impossible to mount file".

'dmesg' says:
"
[99684.179482] attempt to access beyond end of device
[99684.179484] sdb: rw=0, want=4294967292, limit=15319040
"

'sudo fdisk -l /dev/sda' says:
"
Device Boot Start End Blocks Id System
/dev/sdb1               1    69273667  4294967294   ff  BBT
"

How can I mount a 'BBT' file system on Ubuntu?

Thanks a lot!

---

### Post by Stochastic on 2008-10-24
This archived thread details how a sony nwz-s615f is mounted: [http://ubuntuforums.org/archive/index.php/t-819835.html](http://ubuntuforums.org/archive/index.php/t-819835.html)

After the entire thread, the key post is the last one: > I finally tried it and I had to install pmount (sudo apt-get install pmount) and then all I did was pmount /dev/sdb1 WALKMAN

Hope this helps.

---

### Post by Canellas on 2008-10-24
It worked fine!

Thanks a lot!

---

