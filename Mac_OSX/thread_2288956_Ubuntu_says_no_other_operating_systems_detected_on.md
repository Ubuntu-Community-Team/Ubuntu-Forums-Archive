---
title: "Ubuntu says no other operating systems detected on hard drive"
date: 2015-07-30
forum: Mac OSX
---

### Post by James_Martiuk on 2015-07-30
ok so first i wanna say i have been through so many different fourms and i cant find one specific to my problem. I have a 21 inch 2010 imac i recently was dual booting with kali linux but since installed it on my macbook pro so now i would like to dual boot my imac with ubuntu. so i booted into the live cd and erased the 15 gb partition i had kali on then i created a new partition of 100 gb for ubuntu my hardrive is 1tb. I then went ahead and clicked the install ubuntu and got the message about no other operating systems detected. here is what i got from fdisk -l 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      409639      204819+  ee  GPT
/dev/sda2   *    31641600  1747453951   857906176   af  HFS / HFS+
/dev/sda3      1952255592  1953525127      634768   af  HFS / HFS+

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  1953519615   976759807+  ee  GPT
ubuntu@ubuntu:~$ 

this is an image from disks

[ATTACH=CONFIG]263502[/ATTACH]


please any help would be extremly appreciated. Thank you in advance for any help provided.

---

### Post by oldfred on 2015-07-30
Moved to the Apple sub-forum.

I do not know Mac and they are somewhat different than PCs.

Many years ago when Apple converted to Intel CPU, they also started using UEFI. UEFI uses gpt partitioning. 
Now all new Windows systems are UEFI (newer version than older Macs) and have gpt partitioning.

Gpt has a protective MBR so old disk tools like fdisk still see a gpt partition and at least warn a user that drive is already partitioned and not blank. You should use gdisk which is the fdisk for gpt drives.

       sudo gdisk -l /dev/sda
GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

You also want to always boot in UEFI mode and install Ubuntu in UEFI mode.

 [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)
[http://askubuntu.com/questions/580202/refit-refind-grub2-what-is-the-right-way-for-ubuntu-14-10-on-a-mac](http://askubuntu.com/questions/580202/refit-refind-grub2-what-is-the-right-way-for-ubuntu-14-10-on-a-mac)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
      
 Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

---

### Post by James_Martiuk on 2015-07-30
thank you for all the info ill start reading thanks again.

---

### Post by James_Martiuk on 2015-07-31
lol does not seem like anyone cares but if anyone else runs into this issue here is how i got it to work. well first im not using refind. I had it installed before when i was using kali but i had to restore my mac form back up and it apparently wiped it out but i was still able to boot into kali holding the option button i dont really mind the extra button press. Anyway i just selected other options inside the installer which took me to my partitions. I then found the 100gb partition i had created for ubuntu. I then made a 96gb partition as ext4 and a mount point of / then i used the remaining 4gb and turned it into my swap. ran the installer it threw a warning about not making a  boot partition but said if there was a problem i could possibly create one later so just in case i made sure there was a little free space for that Just in case. I let er install and restarted hit my option key and BAM! Macintosh HD my ubuntu boot and my recovery boot were all there sitting pretty. I will say i was sweating through the whole thing. I like to program not play with hard drive partitions.

---

### Post by coffeecat on 2015-07-31
> **James_Martiuk said:**
> lol does not seem like anyone cares

Please do not be so dismissive of other forum members. You first posted only about 3 hours ago. This is an international forum with members from all around the globe. Other people who may have had something to contribute may live in other time zones and may not have been able to read your thread yet. Also - this is a forum of volunteers who have real lives outside the forum. To suggest that people should have your thread as their priority is unwarranted.

Thirdly, only a minority of the forum membership have experience of Apple hardware, so you are asking from help from a limited audience anyway.

---

