---
title: "Booting from raid 1"
date: 2011-06-17
forum: Mythbuntu
---

### Post by itlarson on 2011-06-17
I am planing to move my mythtv to a raid 1 array,consisting of two 2tb drives, which it will boot off of.  i will be roughly following this guide: [http://blog.foobaria.com/2010/05/installing-ubuntu-1004-desktop-with.html]("http://blog.foobaria.com/2010/05/installing-ubuntu-1004-desktop-with.html").  The main difference will be that I will be dividing the raid array into three partitions, for root, home, and swap, so the mount device will be something like /dev/md_d0p1, instead of /dev/md0.  Has anyone done anything like this?  Or does anyone have any thoughts on pitfalls, or things I might need to know?

---

### Post by ian dobson on 2011-06-17
Hi,

My backend boots from a mdadm raid array. I have 4 2Tb drives and partitioned all the drives so that I have a 20Gb partition (for / and boot) and the rest as a RAID5 array.

My kernel boot command has the kernal command line root=/dev/md0 and md0 is defined in mdadm.conf

The most important thing is make sure that you recreate the inital ram disk (with  sudo update-initramfs -u -k all) whenever you change your array.

My tips:-
1) Before you start make sure you have a good boot medium that you can use to boot the box if the array assembling at boot doesn't work.

2) When the system is working, remove one of the drives and make sure the system boots correctly with a degraded array.

Regards
Ian Dobson

---

### Post by itlarson on 2011-06-18
Thanks for the reply.  Would the update-initramfs thing only apply if I modified the raid array?  Since it's a raid 1, there isn't much to modify.  If I need more storage, I can just create a second array, and add it in storage groups.  

I've decided to post what I am doing, as I do it, so I can refer to it in the future, and hopefully provide useful information which might help someone else.  here's what I've done so far.

-I disconnected  my old hard drives, and plugged in two new 2tb Samsung f4 drives.  Darn- forgot to make a copy of my database, so I will have to plug my old drives back in latter, and do that.

-I Booted from the Mythbuntu 10.04 amd 64 live cd.

-I partitioned the drives with one big partition each.  To make sure the 4k sectors are handled properly I used fdisk as follows:
  sudo fdisk /dev/sda
  "u" to toggle the units to sectors
  "n" to create a new partition
  "p" to make it a primary
  "1" for the partition number
  "64" for the start sector
  default for the ending sector
  "w" to write the changes and return to the bash prompt. 
  repeat for /dev/sdb

If anyone is using this method to create more than one partition, it is important that each partition start with a sector number divisible by eight, or the drives performance will be degraded.  The latest gparted is supposed to deal with the 4k sector issue properly, but I am not sure if the one in 10.04 does.

-I installed the raid driver mdadm using "sudo apt-get install mdadm"  

-Now I am building the raid array.  the command is:

"sudo mdadm --create /dev/md1 --verbose --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1".

I can view the status of the build with:

"cat /proc/mdstat"

which produces output like:

Personalities : [raid1] 
md1 : active raid1 sdb1[1] sda1[0]
      1953514432 blocks [2/2] [UU]
      [====>................]  resync = 21.7% (424602304/1953514432) finish=198.5min speed=128317K/sec      
unused devices: <none>

or I can use "watch -n0.2 cat /proc/mdstat" to create a continuous readout of the build progress.  This should take several hours.  when it has compleated, I will install Mythbuntu.

---

### Post by ian dobson on 2011-06-18
Hi,

I recommend running update-initramfs if anything changes that could effect the boot process. It only takes about 10seconds so it's not a major process.

Regards
Ian Dobson

---

### Post by itlarson on 2011-06-18
Other than adding drives, what types of things would do that?

---

### Post by ian dobson on 2011-06-18
Hi,

A short explination:-

When the linux kernel loads, the inital ram disk is also loaded. The kernel then mounts the inital ram disk and executes the init process. This process loads drivers, configures enough of the system so that the root file system can load.

Mdadm uses the mdadm.conf file to assemble drives into RAID arrays. mdadm only reads the configuration file on assembling an array.

As / is mounted on a RAID array, the mdadm.conf file in the inital ram disk must contain the correct information so that mdadm can assemble the array and then init can remount / using the array.

Regards
Ian Dobson

---

### Post by itlarson on 2011-06-18
Thanks for the explination.  In a raid 5 you would need to do this after adding a drive, but I'm still not sure why I would have to do this to a raid 1.  

For some reason the installer is having trouble creating the third partition, so I am starting overwith three raid arrays, each of which will be a single partition.

---

### Post by ian dobson on 2011-06-19
Hi,

I think it's also necessary for a mirrored array, the question is rather unimportant, as a update-initramfs only takes afew seconds.

Regards
Ian Dobson

---

