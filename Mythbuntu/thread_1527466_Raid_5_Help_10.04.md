---
title: "Raid 5 Help 10.04"
date: 2010-07-09
forum: Mythbuntu
---

### Post by DisasterEC on 2010-07-09
Hi,

I have been struggling to get mythtv installed on a raid 5 devices. I have read through differnt methods for the last week.

I was able to set up a raid 5 by using the Ubuntu Maverick 10 amd 64 cd. And boot up everything works fine.

I then decided to go back to the myththv 10.04 cd and try install then. 

I open terminal installed mdadm and ran the mdadm --assemble --scan command.
This enabled me to find the md0 device to install mythtv on. Install went through ok.

Problem is when I boot I get the below error.

> 
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev
ALERT! /dev/disk/by-uuid/8b36fe6b-26fb=40c60-8eef-020aae25f969 does not exist. Dopping to a Shell!I have been looking at fstab and mdadm.conf but I belive I am at the stage where I need help on how to tackle this. I am not sure if I now need a differnt live CD to fix this? Or the steps of how to repair it not finding the raid?

Thanks.

---

### Post by yonkiman on 2010-07-09
I don't know if this will really help you or not, but for my Mythbuntu / RAID 5 system, I installed Mythbuntu on a single non-raid drive, and used a separate raid 5 array for all my mythtv/user data.

The idea being that I could always reinstall Mythbuntu from scratch if that drive failed, and it also made it easier for OS / Mythbuntu upgrades...I just install the new OS onto a different disk (or partition), migrate the MythTV database to it, and pick up where I left off.  If that fails I go back to the original disk (or partition).

The only drawback is that you have to regularly back up your MythTV database to the RAID drive, but that's not too hard and easy to automate.

-Fred

---

### Post by ian dobson on 2010-07-09
Hi,

I don't think you can boot from a mdadm RAID5 array. Maybe setup your box with the following:-

Boot - 20Gb - Mirrored over all drives
Data - Rest - RAID5 array

Thats how I've setup my backend server, and I can say it works really well (Now have 12Tb in 6 Harddisks, Boot,Data,Backup)

Looks as if GRUB2 supports booting from RAID5, have a look here [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1310224](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1310224)

Regards
Ian Dobson

---

### Post by DisasterEC on 2010-07-09
The current error I have is with having a 50mb boot partition on sda1.

I also tried a mirror raid with sad1 and sda2 for the boot partition. Still get the same error :(

---

### Post by ian dobson on 2010-07-10
Hi,

Can you try changing the kernel boot line to use  root=/dev/md0 rather than the UUID, when md0 is your root partition.

Also did you configure your mdadm.conf file correctly?
Did you run update-initramfs -u to rebuild your initramfs after modifying the mdadm.con file?

If your system makes it to the shell you should be able to manually assemble the root RAID array using mdadm, then let the system continue booting. Once the system is booted you can should update your mdadm.conf file and run update-initramfs -u so that the mdadm.conf file gets added to the init fs.

Sorry if I'm abit vage, but I went through this process about 2 years ago when I setup my backend server and can't remember all the details.

Regards
Ian Dobson

---

### Post by DisasterEC on 2010-07-12
Have tried steps in the grub2 but nothing is working.

I think the problem is that /dev/md0 is not been seen or cant be mounted or created. Noidea how to fix this though.

Any detailed steps would be much appreicated. Thanks for help so fair.

---

### Post by ian dobson on 2010-07-12
Hi,

so you get to the busybox prompt. If so run the mdadm --assemble --scan to assemble your array when in the busybox prompt. Then exit busybox which should continue the normal boot sequence.

When the system boot login as root and got to a terminal prompt and type:-

echo 'DEVICE partitions' > /etc/mdadm/mdadm.conf
mdadm  --examine  --scan >> /etc/mdadm/mdadm.conf

this will create the mdadm configuration file. Then type
 update-initramfs -u

this will then create the inital ram disk that the system uses to boot, before it loads the root file system.

Hope this helps
Regards
Ian Dobson

---

