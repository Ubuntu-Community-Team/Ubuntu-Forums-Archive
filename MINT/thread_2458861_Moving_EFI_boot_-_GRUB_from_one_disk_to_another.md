---
title: "Moving EFI boot - GRUB from one disk to another"
date: 2021-03-05
forum: MINT
---

### Post by pintasa on 2021-03-05
First time poster and very newbie so please forgive my ignorance and mistakes.

I was using Linux Mint 18 installed on a 500GB HDD and recently installed LM20 on a 240GB SSD. 

Inspecting the partitions I see the EFI partition of LM20-240GB-SSD is empty so it seems to me the way boot works is that the mobo NVRAM directs to EFI in 500GB HDD where GRUB is located and from there I choose LM20 and sent to the LM20 partition which loads LM20.

This works OK but requires both disks to be operational. For now I want to leave the old disk in place just for data and backups but maybe one day I want to remove it or it just fails.

It seems to me it makes more sense and it is safer to have EFI boot-GRUB in the same LM20-240GB-SSD and better do that now, without urgency, than in an emergency.

I have looked around and found [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It seems to me that if I just physically disconnect the old HDD and run Boot-repair it will make the SSD EFI bootable but there is a good chance I might lose access to the old disk. 

On the other hand, fools rush in where angels fear to tread and I want to be extremely careful and tread very lightly and carefully. 

I want to move GRUB from one disk to another and I want to learn more about the whole booting process.

My thought right now is that the EFI partition in the LM20 SSD is empty and unused so I can try to build it into a bootable partition and cannot really do much damage as long as I do not touch any other partition.

So my idea would be to make the LM20 EFI partition bootable and create an entry in the mobo NVRAM pointing to it. This seems to me like least dangerous because if anything is wrong the old boot sequence through the LM18 HDD should still work. 

In summary: I want to be able to boot into LM20 without having to rely on the other HDD being present and operational. What is the safest way to go about this?

One last note: I know Linux Mint is not Ubuntu but a derivative but I believe with respect to the problem I am presenting here they are identical.

---

### Post by slickymaster on 2021-03-05
*Thread moved to **MINT**.*

---

### Post by oldfred on 2021-03-05
Be sure to have working copy of live installer & know how to add Boot-Repair.
I have done all these commands on my system with various versions of Ubuntu, but not Mint. If issues or typos, you may prevent boot & then have to run full Boot-Repair's advanced mode with total reinstall of grub.

Quick answer, just use Boot-Repair's Advanced Mode to do full reinstall of grub specifying sdb drive.


Lots of details if you want to understand how it all works and some details to manually do it.
Ubuntu's Ubiquity installer only installs grub to first drive.
Not sure if Mint uses the Ubiquity installer. 
Have tested installs of Debian & Fedora and both let me choose my sdb drive as location for UEFI boot & they installed to an ESP on sdb drive. Additional installs of Ubuntu overwrite my main working install's boot in first drive, now an NVMe drive unless I do a work around.

Boot is from UEFI using GUID aka  partUUID. So entry in UEFI must boot to ESP by GUID.
Then with Ubuntu, there is a 3 line grub.cfg entry that boots to the full grub.cfg in your install. With multiple Ubuntu's I have just manually edited that 3 line grub to boot a different install.
You can add a new UEFI boot entry, but Ubuntu's version of grub somewhere is hard coded to use /EFI/ubuntu/grub.cfg. I have changed name in /etc/default/grub and then get a new UEFI entry with a reinstall of grub, but it still booted the /EFI/ubuntu/grub.cfg.

Look at these, your UEFI entry has partUUID(GUID) of ESP.
sudo efibootmgr -v
lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

Not sure where Mint has its entry, with Ubuntu, adjust if Mint using mint:
cat /boot/efi/EFI/ubuntu/grub.cfg

If you just reinstall grub specifying your Mint drive, it will move default boot to new entry.
You can do a full reinstall of grub, use Boot-Repair, or manually use efibootmgr for new UEFI entry & copy ESP on one drive to your other drive.
Using efibootmgr you can give a different name to another entry so you can tell them apart, otherwise it will just overwrite current.

This would create a new UEFI entry to boot "ubuntu" from sda's partition 1 as ESP. You could run this with mint18 as description.
 sudo efibootmgr -c  -w -L ubuntu -d /dev/sda -p1
This would create a new UEFI entry to boot "mint20" from sdb's partition 1 as ESP. But you have to have copied /EFI/ubuntu & /EFI/Boot folders from sda to sdb or reinstalled grub to sdb.
 sudo efibootmgr -c  -w -L mint20 -d /dev/sdb -p1
See this for more details:
man efibootmgr

If you run Boot-Repair and look at its report, it will have run efibootmgr -v, listing of drives with UUIDs & partUUID & output of /EFI/.../grub.cfg.

If you change this and do a total reinstall of grub in UEFI mode to sdb drive, it will create new UEFI entry. Grub uses efibootmgr to add entries to UEFI and uses description form /etc/default/grub. So this is another way to add mint20.
To change name/label in menu change info in quotes to whatever makes sense to you:
sudo nano /etc/default/grub
#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DISTRIBUTOR="mint20"
If you do not have /EFI/ubuntu and it only creates /EFI/mint20, it may not boot. Ubuntu's shimx64.efi or grubx64.efi seem to be hard coded to only boot from /EFI/ubuntu, even it grub re-install created everything required in /EFI/mint20 folder in ESP.

You could then edit /EFI/ubuntu/grub.cfg in sda to directly boot older Mint install by changing UUID &  partition reference.

---

### Post by pintasa on 2021-03-05
> **oldfred said:**
> You can do a full reinstall of grub, use Boot-Repair, or manually use  efibootmgr for new UEFI entry & copy ESP on one drive to your other  drive.
Thank you so much for your detailed post.

I took that phrase which seemed to me the best course of action and it turned out to be immensely simpler than I had ever imagined. 

As I said the EFI partition of the new disk was empty so I started by copying there the EFI folder from another disk. 

I thought I might have to "mark the partition as bootable" (no idea how), edit the NVRAM list, etc. but, as it turned out, when I booted again the BIOS detected the new bootable partition and added it to the list and I booted directly there. 

I checked using efibootmgr and, sure enough, there new entry is there. So this is one of those very rare instances where things are easier than expected. 

Thanks again for your help.

---

### Post by oldfred on 2021-03-05
You normally set a FAT32 partition as the ESP - efi system partition with the esp flag and the boot flag using gparted (right click).
Only one FAT32 as ESP per drive or device. 
Although some have multiple FAT32 with boot files. UEFI will only see one, but grub may let you boot from others.

---

### Post by pintasa on 2021-03-05
> **oldfred said:**
> You normally set a FAT32 partition as the ESP - efi system partition with the esp flag and the boot flag using gparted (right click).
Only one FAT32 as ESP per drive or device. 
Although some have multiple FAT32 with boot files. UEFI will only see one, but grub may let you boot from others.
It seems when I installed LM20 the install created the ESP Fat32 but left it empty and used the one on the old HDD but the partition was there and just copying the EFI folder and files was enough. 

One of those very rare instances in life where things turned out better than they appeared at first.

I think I understand the general lines of the boot process, NVRAM list links to bootable devices via UUID ... but the UUID's I see with efibootmgr in the list do not seem to match the UUID's I see in the drives themselves with the disks app. I am not clear about this.

---

### Post by oldfred on 2021-03-05
UEFI uses GUID aka partUUID.
If you compare partUUID with UEFI entry you will see the same very long number:
sudo efibootmgr -v
lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

---

### Post by pintasa on 2021-03-06
> **oldfred said:**
> UEFI uses GUID aka partUUID.
If you compare partUUID with UEFI entry you will see the same very long number:
sudo efibootmgr -v
lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"
I did not know the lsblk command . Now that I use it I can see the correlation between EFI list and what is mounted. Thanks.```

NAME   MOUNTPOINT                                LABEL   SIZE FSTYPE 
sda                                                    465,8G              
&#9500;&#9472;sda1 /boot/efi                                         512M vfat  
&#9500;&#9472;sda2 /mnt/3b832ec4-fd2d-4824-bb84-6ed19723d3af       457,4G ext4   
&#9492;&#9472;sda3                                                   7,9G swap   
sdb                                                    223,6G        
&#9500;&#9472;sdb1                                                   512M vfat   
&#9492;&#9472;sdb2 /run/timeshift/backup                           223,1G ext4   
sr0                                                     1024M      
```


sda is the old LM18 500GB HDD and 
sdb is the LM20 240GB SSD I am currently running. 

Why does sdb2 mountpoint show [FONT=courier new]**/run/timeshift/backup**?
What does that mean?
[/FONT]

---

### Post by oldfred on 2021-03-06
I use rsync for backup, not timeshift. Someone using timeshift may know.
But it looks like your backup partition?

To get to users that use timeshift, best to post new thread with that in title, so they may look at it.

---

### Post by pintasa on 2021-03-06
I booted up again several times and now the mountpoint is always "/" as it should be. 

I guess it was some glitch or it was doing a backup or something. 

Anyway, I consider the boot issue resolved and I thank you for your help.  I have learned a few things.

---

