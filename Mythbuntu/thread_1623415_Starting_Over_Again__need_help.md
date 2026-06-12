---
title: "Starting Over Again | need help |"
date: 2010-11-16
forum: Mythbuntu
---

### Post by mythB on 2010-11-16
hello :) can someone help me with a new install for my 10.10 desktop edition im about to burn on cd ?
i used an old mythubuntu and updated it and it went all funny on me so im starting again. i got a card it is an asus 7135 fm card with a white color small remote came with it and a wire that plugs into th card and the other end sticks on the front of my tower. i have a 250gig hdd for system drive and a 500gig slave drive for my movies and songs. i want to have cable tv screwed into the card so i can watch tv along with my movies :) i have no clue how to do alot of this stuff with plugins and setting it up but im a good listener :) i have a gt8800 gfx card that is hi definition, so maybe that will be good for movies. i think i will use hardwire instead of wireless and run it from a router and set it up to login with another computer to add movies to it from downloading them will be ok ? thnx for reading.

---

### Post by mythB on 2010-11-16
Install went smooth i like it, only 1 thing is my card was not in the list and the only one i seen that was close was the asus 7131 so i chose that :confused: my cards a 7135, so what do i need to do to make it let my control work ? thanks :)

so far so good

---

### Post by mythB on 2010-11-16
how do i mount my slave drive, when i hooked it up on reboot it said i dont have permission :confused:

also i have only 13 movies on my 500gig and gparted says 247gig is used


update: i rebooted and my remote works but how can i use my slave to watch movies? can anyone help me

---

### Post by mythB on 2010-11-16
sudo fdisk -l  shows this if it helps :confused:


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29255   234983424   83  Linux
/dev/sdb2           29255       30402     9212929    5  Extended
/dev/sdb5           29255       30402     9212928   82  Linux swap / Solaris

---

### Post by CharlesA on 2010-11-16
Don't bump yer thread repeatedly. If you need help on a specific issue, create a thread for that specific issue.

There is plenty of documentation regarding mounting drives in Ubuntu over here: 
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

---

