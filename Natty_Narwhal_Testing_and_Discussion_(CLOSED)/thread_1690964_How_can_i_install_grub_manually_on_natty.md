---
title: "How can i install grub manually on natty?"
date: 2011-02-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by aviramof on 2011-02-19
Via live cd of course.

i tried this but it didn't worked:

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev  /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo  chroot /mnt

Code:

sudo grub-install /dev/sda

Code:

sudo grub-install /dev/sdb
```

Thanks in advance.

---

### Post by kansasnoob on 2011-02-19
You have two typos. An extra space here:

sudo mount --bind /dev  /mnt/dev

and again here:

sudo  chroot /mnt

Should be:

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

---

### Post by aviramof on 2011-02-20
How can manually update grub via live cd?

update-grub doesn't work.

---

### Post by Harry33 on 2011-02-20
> **aviramof said:**
> How can manually update grub via live cd?

update-grub doesn't work.

If you use another system, like Live-CD or Live-USB, you need to chroot into the target system. You see if you run update-grub from Live-CD, it means the CD-system would upgrade its own grub, and yes it does not succeed.

---

### Post by kansasnoob on 2011-02-21
> **aviramof said:**
> How can manually update grub via live cd?

update-grub doesn't work.

Generally you need to add one more bit to that, "sudo mount --bind /sys /mnt/sys".

You see the "space&&space" is just a way of combining commands. What I posted before:

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

Is the same as running each of these commands individually:

```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
```

In order to be able to update-grub while reinstalling it you'd add the "sudo mount --bind /sys /mnt/sys" bit just before "sudo chroot /mnt":

```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Or:

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
```

If you need to perform any package management or such in a chroot you need to add a bit more:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

---

### Post by aviramof on 2011-02-21
Thanks for all your help.

---

### Post by aviramof on 2011-02-22
When i try the commands 

sudo grub-install /dev/sda  Code:  sudo grub-install /dev/sdb

i get usr/sbin/grub-probe: error: cannot stat `aufs'.

---

### Post by psusi on 2011-02-23
> **aviramof said:**
> When i try the commands 

sudo grub-install /dev/sda  Code:  sudo grub-install /dev/sdb

i get usr/sbin/grub-probe: error: cannot stat `aufs'.

You didn't follow the commands listed above.  Specifically you did not chroot.

The chroot method installs the version of grub on the hard disk.  It is easier to install the version on the livecd:

```

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

---

### Post by drs305 on 2011-02-23
If you haven't had grub 2 on your system previously, or purged it, using just the "grub-install" command is not enough. Although it sounds like what you may need, it deals only with a few aspects of installing the grub package (MBR, *.mod files, core.img and some others). 

To install the full Grub2 package in a chroot environment, run:
```
sudo apt-get install grub-pc
```
which will install the Grub2 (*grub-pc*) and, if needed, *grub-common* packages.

---

