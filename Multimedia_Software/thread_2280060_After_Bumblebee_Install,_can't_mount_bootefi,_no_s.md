---
title: "After Bumblebee Install, can't mount /boot/efi, no sound, USB keyboard does not work"
date: 2015-05-27
forum: Multimedia Software
---

### Post by psjf3635 on 2015-05-27
I have a Lenovo IdeaPad Z710 laptop on which I have Kubuntu 14.10 dual-booting with Windows 8.1. It's one of the models that use Nvidia's Optimus system to switch between the integraded Intel HD 4600 graphics chipset and the Nvidia GT 745M chipset.

I was having issues with the default Nouveau video drivers, so I attempted to install Bumblebee using [these instructions]("https://wiki.ubuntu.com/Bumblebee") on the Ubuntu Wiki. While the drivers were installing, the system locked up completely for over an hour, so I forced a shutdown and rebooted back into Kubuntu. While it was booting, I got an error message to the effect of "/boot/efi could not be mounted. Press S to skip or press M for manual recovery." I pressed S to skip and Kubuntu finished booting, so I ran ```
# dpkg --configure -a
``` to finish the installation. After another reboot, I got the same error as before, but the installation otherwise seemed to be successful...until I realized I had no sound, neither through the built-in speakers nor through the audio output jack.

Today, I booted into Kubuntu again, only to find that in addition to the previous issues, my computer would not register input from my USB keyboard, although it would register input from both the built-in keyboard and another USB keyboard. It is not the keyboard itself, as it still works fine in Windows. The behaviour is also independent of the USB port to which the keyboard is connected. After a quick look at lsusb, it appears that the keyboard is being recognized as connected but not identified:

lsusb output without keyboard plugged in:
```
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 006: ID 8087:07dc Intel Corp. 
Bus 003 Device 004: ID 5986:0295 Acer, Inc 
Bus 003 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 003 Device 017: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

lsusb output with keyboard plugged in:
```
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 006: ID 8087:07dc Intel Corp. 
Bus 003 Device 019: ID 2516:0004  
Bus 003 Device 004: ID 5986:0295 Acer, Inc 
Bus 003 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 003 Device 017: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

In case it's useful, here's the output of fdisk -l and the contents of /etc/fstab:
```
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 3EC894F0-84E3-4C69-944D-C53BC104154D

Device          Start        End   Sectors   Size Type
/dev/sda1        2048    2050047   2048000  1000M Windows recovery environment
/dev/sda2     2050048    2582527    532480   260M EFI System
/dev/sda3     2582528    4630527   2048000  1000M unknown
/dev/sda4     4630528    4892671    262144   128M Microsoft reserved
/dev/sda5     4892672  969773055 964880384 460.1G Microsoft basic data
/dev/sda6  1872435200 1924863999  52428800    25G Microsoft basic data
/dev/sda7  1924864000 1953523711  28659712  13.7G Windows recovery environment
/dev/sda8   969773056  985774079  16001024   7.6G Linux swap
/dev/sda9   985774080 1872435199 886661120 422.8G Linux filesystem

Partition table entries are not in disk order.

```

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda9 during installation
UUID=f88479eb-302d-4749-a079-ab3585c374af /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=5C83-B328  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda8 during installation
UUID=c2a4c01f-828d-4d7c-a075-2eaf9e989e58 none            swap    sw              0       0
# Mount Windows partition for access to documents
UUID=E2348A5A348A3199   /home/psjf/.media/win8/       ntfs    rw,relatime,users,exec,data=ordered     0       1
# Bind Windows document directories to directories in ~
/home/psjf/.media/win8/Users/psjf/Documents/        /home/psjf/Documents/ none    bind    0       0
/home/psjf/.media/win8/Users/psjf/Downloads/        /home/psjf/Downloads/ none    bind    0       0
/home/psjf/.media/win8/Users/psjf/Games/    /home/psjf/Games/     none    bind    0       0
/home/psjf/.media/win8/Users/psjf/Music/    /home/psjf/Music      none    bind    0       0
/home/psjf/.media/win8/Users/psjf/Pictures/ /home/psjf/Pictures   none    bind    0       0
/home/psjf/.media/win8/Users/psjf/Videos/   /home/psjf/Videos     none    bind    0       0

```

Thanks in advance for any help with these issues.

---

### Post by NoWayWin8 on 2015-05-28
I don't know about bumblebee but your fstab bind entries for aren't using the right mount-points for directories on the Windows partition,
/home/psjf/.media/win8/Users/psjf/ is not a mount point.

Better to reference disks as /dev/disk/by-uuid/....

---

### Post by psjf3635 on 2015-05-30
I think you're misunderstanding. What I'm doing there is mounting my Windows partition to /home/psjf/media/.win8/, then binding certain directories on that partition to folders in my home directory.

At any rate, whether I've done it the "best" way or not, it's been set up that way pretty much since I've had Kubuntu installed and it's always worked perfectly. I don't think it's what's causing the problems.

---

### Post by psjf3635 on 2015-05-31
Well, I've solved all my problems, although I'm not sure why this worked.

Somehow my user account had been removed from the audio, pulse, and pulse-access user groups. I also checked the "Additional Drivers" dialog on a whim, and found that even though I had installed the Nvidia drivers, it was still set to use Nouveau. I fixed both of these issues and rebooted, and suddenly all my problems were fixed: I no longer get the message about /boot/efi, and my sound and keyboard both work again. So I'm going to go ahead and mark this thread as resolved, even though I don't understand why either of those things would affect mounting partitions or recognizing my keyboard.

---

