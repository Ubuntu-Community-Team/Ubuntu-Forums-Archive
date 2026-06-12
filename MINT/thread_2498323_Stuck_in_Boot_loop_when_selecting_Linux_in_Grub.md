---
title: "Stuck in Boot loop when selecting Linux in Grub"
date: 2024-06-09
forum: MINT
---

### Post by santialur on 2024-06-09
Hi all. I am stuck in a boot loop on a new Linux Mint install.   
     (Microsoft Surface Laptop Go 3   
     Some context:   


[LIST]
[*]          Had windows and installed Ubuntu (in order to dual boot) yesterday  but Windows would skip Grub so I ran this command (yeah I know):   

     bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi   

[*]          After this, nothing worked and I ended up in a command line every time I restart the pc.   

[*]          I decided then that I would create another USB but this time using  Linux Mint, and I did a fresh install using the option "Erase disk and  install Linux Mint".   
[/LIST]
     It seemed to have installed it correctly but now I am stuck in a  loop where I see the GRUB options, I select Linux Mint, and then it  restarts the computer again.   


[LIST]
[*]          The only ways for me to get into Linux Mint are:
      - selecting the UEFI  option on Grub, and then tell the laptop to boot immediately using the  selected option and then it loads  Mint correctly.
      - on grub, typing "c", which goes into a command line, then I press exit; which restarts the pc, and then I see grub and I select Mint and it loads correctly. 

[/LIST]
     
I ran boot-repair with no success, and it gave me this paste bin:   

     [https://paste.ubuntu.com/p/rVrTFKB68r/](https://paste.ubuntu.com/p/rVrTFKB68r/)   

     
Thanks everyone! this has been a frustrating experience

---

### Post by wildmanne39 on 2024-06-09
Welcome to the forum, thread moved to the Mint sub-forum.

---

### Post by yancek on 2024-06-09
> ERROR: unsupported sector size 4096 on /dev/dm-1

If you do an online search for the error above you will find it is related to using RAID.  I see you are also using LVM.  Have you done RAID/LVM installs before or do you have a particular tutorial you used you could link to for installing using LVM and RAID which you could post?

---

### Post by oldfred on 2024-06-09
Report did not show if UEFI Secure boot was on or not. It usually does.
[FONT=monospace][COLOR=#000000]sudo mokutil --sb-state

You can totally delete Windows entry as it refers to a partUUID that does not exist.
It also has a grub entry rather than a normal Windows boot entry. That is sometimes done with systems that only want to boot Windows by description. If yours needs that you need to recreate with correct partuuid for new ESP - efi system partition you created when you reinstalled.
see this for efibootmgr info:
man efibootmgr
To delete an entry like 0005, double check entry is correct.
sudo efibootmgr -v
sudo efibootmgr -b XXXX -B 
[/COLOR]
Report also did not show if ESP mounted in fstab.
cat /etc/fstab

If mounted in fstab, you can just reinstall grub or use efibootmgr to create new "Windows Boot Manager" entry that uses grub.


[/FONT]

---

### Post by santialur on 2024-06-09
I may have sound very proficient on my post but I am[FONT=arial][/FONT] a total noob with Linux. I had done installs in the past but they just went smoothly so I don't know what is required to do here. Here's my cat /etc/fstab:

[FONT=courier new]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/vgmint-root /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=3790-3AC0  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/vgmint-swap_1 none            swap    sw              0       0

[/FONT]

---

### Post by yancek on 2024-06-12
From your earlier description and information, have you gone into the BIOS firmware on boot and selected the Boot0004 option (ubuntu) to boot Mint as the first boot priority in the BIOS.  Also, as asked before, are you familiar with LVM/RAID installs?  Did you deliberately select to do that type install?

---

