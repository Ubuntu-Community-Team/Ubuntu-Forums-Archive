---
title: "no menu.lst  in GRUB"
date: 2011-04-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jonlucc on 2011-04-20
I just installed Natty on my laptop alongside Win7.  I want to change the boot priority and everything I've read said to edit the /boot/grub/menu.lst file, but it doesn't exist on my system.

---

### Post by uRock on 2011-04-20
Moved to Natty Narwhal Testing and Discussion.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) may be helpful.

---

### Post by Sworddragon on 2011-04-20
On the current GRUB version it is /etc/default/grub.

---

### Post by terry_gardener on 2011-04-20
> **jonlucc said:**
> I just installed Natty on my laptop alongside Win7.  I want to change the boot priority and everything I've read said to edit the /boot/grub/menu.lst file, but it doesn't exist on my system.

you can also install startup-manager to do this.

---

### Post by kansasnoob on 2011-04-20
Assuming you can boot into Ubuntu simply run:

```
sudo update-grub
```

If that fails to find Windows please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by manzdagratiano on 2011-04-20
If this was an install from scratch then Natty most certainly has grub2, which may be checked by:

```
$ apt-cache policy grub2
$ apt-cache policy grub-pc
```

depending on which package was installed - they both refer to the same one, except that grub-pc is a metapackage.

That said, you should first take a look at:
[URL="https://help.ubuntu.com/community/Grub2"]
https://help.ubuntu.com/community/Grub2[/URL]

and then, after running:

```
$ sudo update-grub
```

if Windows still does not show up, first check the partitions:

```
$ sudo fdisk -l
```

When you have ascertained which partition Winblows lies in, say /dev/sda2, then investigate the outputs of:
```

$ sudo os-prober /dev/sda2
$ sudo linux-boot-prober /dev/sda2
```

If one of them is not telling you what's on there, then that is a bug which needs to be reported. I am myself having certain issues with linux-boot-prober duplicating entries which I reported on Launchpad - Bug #758887

---

### Post by jonlucc on 2011-04-21
> **Sworddragon said:**
> On the current GRUB version it is /etc/default/grub.
Thanks!  That solved it.

---

