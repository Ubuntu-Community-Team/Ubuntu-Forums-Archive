---
title: "&quot;update-grub&quot; fails when running Ubuntu installed on a Btrfs subvolume"
date: 2010-08-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by emil.s on 2010-08-06
I have installed Ubuntu, taken a snapshot, and started Ubuntu from that snapshot:
```
root@MobileCommand: ~ #> mount
/dev/sda2 on / type btrfs (rw,subvol=ubuntu_root)
/dev/sda1 on /boot type ext4 (rw,commit=0)
```

But now I can't make a new grub-config:
```
root@MobileCommand:~# update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```

I guess this will break apt when a new kernel arrives... 

Any idéa on a fix/workaround?

---

### Post by ranch hand on 2010-08-06
I think that your problem is installing ubuntu / and /home on btrfs.  I think that / may need to be installed on ext4(3) so that the terminal is able to deal with the /boot partition.

Just a guess really.  I would say that you could test this by chrooting in from the live session and running update-grub from there.  If that works I would say that the / partition format is the problem.

---

### Post by kansasnoob on 2010-08-07
> **ranch hand said:**
> I think that your problem is installing ubuntu / and /home on btrfs.  I think that / may need to be installed on ext4(3) so that the terminal is able to deal with the /boot partition.

Just a guess really.  I would say that you could test this by chrooting in from the live session and running update-grub from there.  If that works I would say that the / partition format is the problem.

+1!

[https://wiki.ubuntu.com/MaverickMeerkat/TechnicalOverview#Installation](https://wiki.ubuntu.com/MaverickMeerkat/TechnicalOverview#Installation)

> The new btrfs file system may now be used during installation via manual partitioning, as long as /boot is on some other file system.


I've so far just used a separate /boot partition with ext4 :)

---

### Post by emil.s on 2010-08-08
> **kansasnoob said:**
> 
I've so far just used a separate /boot partition with ext4 :)

Which I have to.. :) (se first post)

Seems like there are some problem with "grub-probe":
```
root@MobileCommand: /mnt #> grub-probe /
grub-probe: error: cannot find a device for / (is /dev mounted?).
root@MobileCommand: /mnt #> grub-probe /mnt/ubuntu_root/
grub-probe: error: unknown filesystem.
```

/mnt/ubuntu_root is the / if mounting sda2 as a regular device:
```
root@MobileCommand: /mnt #> mount | grep sd
/dev/sda2 on / type btrfs (rw,subvol=ubuntu_root)
/dev/sda1 on /boot type ext4 (rw,commit=0)
/dev/sda2 on /mnt type btrfs (rw)
/dev/sda1 on /mnt/ubuntu_root/boot type ext4 (rw)
/dev/sda1 on /mnt/boot type ext4 (rw)
```

Any ideas?

I guess this is not supported, but I have no plans to make it stop me. ;)

Maybe there is a newer btrfs patch för grub that I can test?

---

### Post by emil.s on 2010-08-28
Running from live CD now and testing from an chroot, but that makes no difference...

I have of course mounted /dev in the chroot to.

---

### Post by cariboo on 2010-08-28
If you chroot just the /boot partition, does it work? I don't plan on trying btrfs until natty.

---

