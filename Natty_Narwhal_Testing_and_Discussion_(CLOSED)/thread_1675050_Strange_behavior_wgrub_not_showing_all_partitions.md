---
title: "Strange behavior w/grub not showing all partitions"
date: 2011-01-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2011-01-24
A triple boot with Win7, Maverick and Natty. 
After updating a kernel or installing a new kernel and update-grub is ran, it seems to be missing my Maverick partition
This first happened yesterday and I was gonna post boot script info BUT after running the boot script info and doing an 'update-grub, my maverick partition is showing itself again in grub. I installed a newer kernel again today and Maverick partition was not showing in grub again. So I ran the boot info script again and for just the sake of doing it, I ran update-grub again and Maverick partition was in grub again.
So my question is why would running the boot info script make my Maverick partition appear again in grub.
I know this sounds strange but it is really bugging me.
If some one needs me to explain a little more, let me know please.

---

### Post by Quackers on 2011-01-24
This happened with an earlier version of grub iirc but it sorted itself out. No idea what happened though :-)

---

### Post by dino99 on 2011-01-25
have some issue on my side too, and have digg around a little then reported againt os-prober. Maybe you hit the same problem.

[https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/704538](https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/704538)

---

### Post by efflandt on 2011-01-25
Where do you have grub for Maverick and Natty?  If both use your main mbr, that might be an issue, because grub has changed somewhat (but not sure if the mbr part has).

I have Maverick and its grub on primary partition sda4, with that partition marked as boot partition using Win7 mbr on sda (because Dell Datasafe I think stepped on grub on mbr of sda).  Although, I installed Natty on sdb1 with its grub in mbr of sdb, which I currently boot from.

So if Maverick updates its kernel, Natty grub is not going to know about that unless I do sudo update-grub in Natty.  If Natty updates its kernel or grub, no problem, because I am booting from Natty's grub on sdb.

```
efflandt@natty-ssd:~$ **sudo os-prober**
/dev/sda2:Windows 7 (loader):Windows:chain
/dev/sda4:Ubuntu 10.10 (10.10):Ubuntu:linux
```

---

### Post by DougieFresh4U on 2011-01-25
```
sudo] password for dougie: 
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda7:Ubuntu 10.10 (10.10):Ubuntu:linux
```
All 3 partitions are showing in grub.
What I thought was odd that after running 'boot info script' when only 2 partitions were showing in grub that boot info script magically fixed and all 3 showing afterward

---

