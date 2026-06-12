---
title: "raid 1 help"
date: 2009-04-28
forum: Mythbuntu
---

### Post by 4dognight on 2009-04-28
I have moved my mythbuntu master backend to a pair of 1TB drives. I was hoping to mirror it for rendundancy. My drives will be setup with 3 partitions.

sda1 as / ext3-> 20 gb
sda2 as swap -> 1gb
sda3 as /var/lib/mythtv xfs->remainder of disk

the second drive sdb1-3 is setup the same.

I have a third non mirrored drive to hold just recordings, mounted as /var/lib/mythtv/recordings. This is to avoid drive contention while recording/playback tv recordings from the music/video/backup directorys on the main drives. Im not worried about losing recordings. But I dont want to lose any music/video/pictures/backups.

I used the software raid driver and utilities provided by mdadm.
I am setting the 3 arrays as

md0 = sda1 sdb1 /
md1 = sda2 sdb2 swap
md2 = sda3 sdb3 /var/lib/mythtv

I was succesful in getting md1 and md2 created. 
the problem is with md0. I used the tutorial I found at [http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch)

When I reboot now , I get an error 22 from grub when it tries to boot from hd1,0 . I think it then falls back to hd0,0. My system comes up and both md0 and md2 are visible from a df -h cmd. So I think it is booting from h0,0, then is mounting the md0 array when it comes up. Which only contains sdb1 at the moment. As, when I try to add sda1 to the md0 array, I am getting a devce busy error on sda1. It s kind of a catch 22.

my grub entries are the same on both sda1 and sdb1. Im kind stuck in the midst of setting up md0. I cant procedd further until I can get it to boot from hd1,0 , so I can add sda1 to md0.
the 2 entrys are,

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=/dev/md0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0b0e7143-7213-4d7b-814c-ce0426c2da8a ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

---

### Post by ian dobson on 2009-04-28
Hi,

I'm currently upgrading my backend server to 4x2Tb WS drives and was in exactly the same position as you.

If you can boot from the second menu option, go to /boot/grub and edit device.map so that you see the line:-
(HD0) /dev/sda

Then run update-grub (or is it grub-update), this will display messages that it's installing grub on your mirrored drives (sda1 and sdb1).

Note: I removed the "root (hd1,0)" from the menu.lst as it didn't seem to make any sense to me (root is on /dev/md0).

NOTE: This is all from memory, I finally got my new system to boot at about 4am on sunday morning and the details are abit vage (Too much coffee and not enough sleep).

Regards
Ian Dobson

---

### Post by 4dognight on 2009-04-28
> **ian dobson said:**
> Hi,

Note: I removed the "root (hd1,0)" from the menu.lst as it didn't seem to make any sense to me (root is on /dev/md0).

Regards
Ian Dobson

That is what I was thinking too. Why would I want to have two lines, one to boot from sda1 and the other sdb1 , when I am using md0. Im thinking that if one of the drives fail it will still boot from md0, as the other drive is still available. 

The error I get though when booting from md0 is , Error 22 No such partition.  I have checked and there is a /dev/md0. 

Does something need to be loaded in the booting process that makes /dev/md0 usable, since its a software array?

I will try as you did tonight. But Im still a bit confused on how it knows about /dev/md0 so early in the boot process.

One other thing, should I be using the UUID for /dev/md0?



thanks for the input.

---

### Post by ian dobson on 2009-04-28
Hi,

You need to regenerate the inital ram disk, including the md and raid1 modules.

I used /dev/md0 as the root command line for the kernel. I removed the line "root (hd1,0)"  from menu.lst

After editing device.map I just ran update-grub which seemed to work for me, don't ask my why, I'm still learning :)

Regards
Ian Dobson

---

### Post by 4dognight on 2009-04-28
OK, I got partial success.

I still have 2 stanzas in menu.lst. One is for hd1,0 and the second is hd0,0
I also changed it to use /dev/md0 on both.
I did issue a update for the ramdisk.

I then rebooted. I still got Error 22 : on reboot. But when it then tried hd0,0 it booted. And this time it used /dev/md0(I previously still had sda1 for hd0,0 stanza) So this time I could use mdadm to add sda1 to my md0 array. 

Now , I still need to figure out why it cant boot off of hd1,0. But at least it now boots off hd0,0 and my md0 array is sync'd and working.

Im guessing maybe my MBR is not installed on /dev/sdb? Does that sound right? 

I used the following to create the sdb drive

sfdisk -d /dev/sda > sda.out
sfdisk /dev/sdb < sda.out

then to copy data I used

cp -dpRx / /mnt/md0   (/dev/md0 was temp mounted on /mnt/md0)

Did I miss something?

---

### Post by ian dobson on 2009-04-28
Hi,

A missing mbr would mean that grub wouldn't even start.

Have you added sdb to your raid array using mdadm? If sdb isn't in an array (md0) then the partition table might not be correctly configured.

Regards
Ian Dobson

---

### Post by 4dognight on 2009-04-28
yes, my md0 array now contains both sda1 and sdb1. Output from /proc/mdstat shows its functioning normal. I can post the output later, from the command.

I could leave all as it is now. It does boot, but only from the hd0,0 stanza in menu.lst. My worry is that if I lose the first drive(/dev/sda). I wont be able to boot, even though the array will still have /dev/sdb.

---

### Post by ian dobson on 2009-04-28
Hi,

Did you modify device.map and run update-grub?

Thats's the only thing I can think of. The system should boot from the menu option title Ubuntu 8.04.1, kernel 2.6.24-22-generic

No matter which drive is active.

One thing I can remember is that I had to edit /etc/initramfs-tools/conf.d/mdadm and change the line BOOT_DEGRADED=false to read BOOT_DEGRADED=true and then recreate the init ram disk.

Regards
Ian Dobson

---

### Post by 4dognight on 2009-04-28
No luck in getting it to boot from hd1,0. It always gets the error 22: no such partition error. Then boots from hd0,0. 

here is my stanzas from menu.lst

title           Ubuntu 8.04.1, kernel 2.6.24-22-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-22-generic root=/dev/md0 ro quiet splash
initrd          /boot/initrd.img-2.6.24-22-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-22-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-22-generic root=/dev/md0 ro quiet splash
initrd          /boot/initrd.img-2.6.24-22-generic
quiet


And here is my device.map

(hd0)	/dev/sda
(hd1)	/dev/sdb

I have run update-grub and update-initramfs -u

---

### Post by 4dognight on 2009-04-29
Figured it out. 

I had to rearrange the boot order in the bios to match grub. If that makes any sense. Any way I dont get the error 22 anymore from grub.

Thanks for the help Ian

---

