---
title: "Natty Grub2 Problems"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Bobhuber on 2011-04-01
I wonder if anyone else is having this problem. The grub2 installed with Natty is hit and miss on seeing and mounting other partitions and drives. I run 10.10 on sda1 and natty on sdb1.
I let Natty reinstall grub2 and half of the time neither operating system would see or mount drives set up in fstab. By reinstalling grub2 from the 10.10 live CD and updating grub both systems now boot normally and recognize all partitions.

---

### Post by Helkaluin on 2011-04-01
Are you using BTRFS as root?

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/732149](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/732149)

---

### Post by jerrylamos on 2011-04-01
> **Bobhuber said:**
> I wonder if anyone else is having this problem. The grub2 installed with Natty is hit and miss on seeing and mounting other partitions and drives. I run 10.10 on sda1 and natty on sdb1.
I let Natty reinstall grub2 and half of the time neither operating system would see or mount drives set up in fstab. By reinstalling grub2 from the 10.10 live CD and updating grub both systems now boot normally and recognize all partitions.

That's why I've got a Maverick or Lucid partition on each of my test systems.  

Once or twice Natty Grub 1.99 made sense, but more frequently it will say I've got a Lucid on /dev/sda6, a Maverick on /dev/sda6, and a Natty also on /dev/sda6.  None of which will boot.

All three on the same partition?!

So I do my best to find some other Ubuntu that will boot, besides Natty, and then run update-grub and grub-install. 

Jerry

---

### Post by Bobhuber on 2011-04-01
> **Helkaluin said:**
> Are you using BTRFS as root?

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/732149](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/732149)

No while that bugs matches the problem exactly I'm using etx4 on 10.10 and 11.04

---

### Post by Helkaluin on 2011-04-01
Fire another bug report then? Remember to include the details.

---

