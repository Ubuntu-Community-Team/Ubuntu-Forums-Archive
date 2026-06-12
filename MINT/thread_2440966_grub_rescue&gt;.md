---
title: "grub rescue&gt;"
date: 2020-04-17
forum: MINT
---

### Post by joni22u on 2020-04-17
Hello everyone,
I recently installed Ubuntu 18.04 on my HP laptop. But after some weeks i got bored and thought to install Linux Mint 19.3. I deleted the Ubuntu partition and after restart my laptop shows grub rescue>
I have the installation media but I can't boot into it.
Pls help!!!

---

### Post by slickymaster on 2020-04-17
*Thread moved to **MINT**.*

---

### Post by oldfred on 2020-04-17
It is defaulting to boot internal drive with grub. But that only will work if you still had Ubuntu partition.
So the only way you can boot is using flash drive with Mint.

You have to select that from UEFI/BIOS boot menu.
If flash drive incorrectly made, then it may not be in UEFI menu and you have to remake it & verify it is correct.

---

### Post by joni22u on 2020-04-18
Which I dont have the ubuntu partition either the flash drive with mint. My flash drive only contains windows 10 bootable usb. But I can't boot to the usb. When I press F9 on my keyboard with the usb plugged in it takes more the usuall to take me to the boot menu. But without the usb it boots normally.

Because if I had the flash drive with mint I would have fixed it by now.

---

### Post by oldfred on 2020-04-18
If your Windows has the repair/recovery console (maybe f8) then you should be able to run Windows repairs.
Windows 10 repair disk
[https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795](https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795)
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)
Rescatux live cd with a grub restore option (through rescueapp) fixed it!
Will now repair Windows BIOS & UEFI
[https://askubuntu.com/questions/1058806/tried-to-install-both-windows-and-ubuntu-now-neither-will-boot](https://askubuntu.com/questions/1058806/tried-to-install-both-windows-and-ubuntu-now-neither-will-boot)

---

### Post by yancek on 2020-04-18
In post one you indicate you "have the installation" media indicating your intention to install Mint.  In post 4 you state that you only have a windows installer on the usb but that if you remove the usb you can boot windows, is that correct?  I'm not sure I see what the problem is.  In post 1, you specifically stated that you obliterated your Ubuntu install so obviously, you can't boot what doesn't exist.   Boot windows, put a usb in the drive and create the Mint boot usb after downloading it.

---

### Post by joni22u on 2020-04-18
@yancek
I was trying to mention that after uninstalling ubuntu I would install mint. Sorry if I messed it up.

And I have the installation media with windows, which I think may be corrupted because my laptop doesn't boot into it.

No I can't boot windows. When I plug the installation media it takes longer to boot into the boot menu. Without the usb it boots normally which means on grub rescue> and even when I insert the usb it boots to 
Grub rescue>
Just to make it clear

When I press F8 it just takes me to 
Grub rescue>

---

### Post by yancek on 2020-04-18
>  I was trying to mention that after uninstalling ubuntu I would install mint

There is never any need to uninstall and in fact, an operating system can't be uninstalled the way you uninstall some software application.  All you would do to repalce Ubuntu with Mint is to download the Mint iso, create a bootable USB or DVD, boot from it and install it to the same partition on which you had Ubuntu.  You would then havee a bootable Mint OS w/no disruption and if you did have problems, you would have the 'live' Mint to try to make repairs.

Do you have the windows installer on a USB and have you changed the boot order in the BIOS to boot from it?  If your windows USB/DVD is corrupted, there is nothing anyone here can do.

---

### Post by joni22u on 2020-04-20
Case closed! Thanks everybody who tried to help me. I finally created a ubuntu bootable usb with my phone and fixed the problem.

---

