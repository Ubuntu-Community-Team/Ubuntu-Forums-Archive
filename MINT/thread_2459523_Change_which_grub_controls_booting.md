---
title: "Change which grub controls booting"
date: 2021-03-20
forum: MINT
---

### Post by bwgolling on 2021-03-20
I added another Mint distro to a computer that was set up for Linux and windows already.  My problem is that I want to use the original linux distro.  I was able to change config in the controlling grub to boot the last successful boot but I would prefer to use everything from the distro that I am using.  I dont want to reinstall the whole thing but can I just reinstall grub or at least change its configuration.  I downloaded boot-repair but I am hesitant to use it until I know for sure that it wont wreck the whole thing.
Any advice?

Is it within the realm of possibility to run Ubiquity from the point only where Grub is installed?  That always works flawlessly when I install a distro.  Basically I want everything left alone except that I want to reinstall grub.

---

### Post by tea for one on 2021-03-20
> **bwgolling said:**
>  My problem is that I want to use the original linux distro.

What is this distro?

---

### Post by bwgolling on 2021-03-20
Sorry.  Both are linux mint.  just different de's

---

### Post by howefield on 2021-03-20
Thread moved to the "*MINT*" forum.

---

### Post by oldfred on 2021-03-20
[FONT=arial]I think Mint uses Ubuntu as boot entry, not a unique entry in UEFI or ESP - efi system partition.

I have reinstalled grub from main working install, but now just manually edit /EFI/ubuntu/grub.cfg.
Ubuntu sets mount of ESP in fstab with [COLOR=#000000]umask=0077 which prevents editing. You can use live installer or edit fstab with defaults & reboot.
I often change to defaults, but that may leave me open to security issues.
[/COLOR]```
[COLOR=#000000][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /boot/efi/EFI/ubuntu/grub.cfg [/COLOR]
search.fs_uuid 54029c4f-0cbe-413e-80ce-78a4995b0551 root  
set prefix=($root)'/boot/grub' 
configfile $prefix/grub.cfg
[/COLOR]
```[/FONT][FONT=monospace][FONT=arial][COLOR=#000000]

You can see what UUID to use with blkid or this:
lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

If you have two drives with an ESP on second drive:
I often install to a second drive and put the test install's UEFI entry into ESP on that drive, keeping my main working install's ESP unchanged, so I do not have to edit it.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
[/COLOR]Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

I also like to turn off os-prober and only have the boot entries I want in 40_custom.
How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[/FONT]
[/FONT]

---

### Post by bwgolling on 2021-03-20
Thanks very much for the help.  I think I can see what's up.  Before I try though I think i will do some studying of grub docs.  I'm tired of getting into this mess and having to stumble my way out of it.
Your advice is very good and already gives me some understanding.
Bruce

---

### Post by yancek on 2021-03-20
The second install of Mint overwrote the grub files in the EFI partition from the first install because the directory created there is named "ubuntu".  Same with other major derivatives of Ubuntu  As stated above, the simplest solution is for you to use the blkid command to get the correct UUID of the drive/partition of the Mint you want booting and then as root (using sudo) mount the efi partition and replacee the current UUID in the grub.cfg file with the correct one.  Oldfred showed you an example of the file, very simple to do.

---

