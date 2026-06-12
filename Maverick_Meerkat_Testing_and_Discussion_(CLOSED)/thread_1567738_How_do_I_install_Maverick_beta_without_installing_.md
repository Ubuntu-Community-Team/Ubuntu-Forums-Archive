---
title: "How do I install Maverick beta without installing its version of Grub?"
date: 2010-09-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jaycee23 on 2010-09-04
I have Win 7 and Karmic as a dual boot. I have had various issues with Lucid so wanted to try the beta version of maverick.

I have created separate partitions for Maverisk to install its root and home partitions but I don't want it to install grub as I am happy to continue using Karmic's grub which currently controls my boot up.

In previous versions at installatio there was an option not to have the bootloader installed but on Maverick this option is no longer available.

Do I just install the bootloader to the root partition of Maverick?

Please help as I do not want to screw up my current dual boot system but would like to try Maverick.

:-)

---

### Post by Starks on 2010-09-04
The devs are working on this. I'm not sure if it's fixed in the latest dailies, but an advanced installation menu is on the way that will let you control where the bootloader goes or whether you even want one installed.

---

### Post by ranch hand on 2010-09-04
There are few things in a prerelease OS that should not be a concern to anyone installing them.

In this case I think you are being overly cautious.  The version of grub that 10.04 uses is much better than the version in 9.10.  I have installed the 10.10 version on my 9.10 install for that very reason.

You will be able to get to your 9.10 install on the first boot.  If you want that grub to be the one you are using just, from the terminal in 9.10, run;
```

sudo update-grub

```
to get your new install on it and;
```

sudo grub-install /dev/sda

```
You need to edit the sda to match your system (could be sdz for all I know).

---

### Post by VMC on 2010-09-04
> **jaycee23 said:**
> I have Win 7 and Karmic as a dual boot. I have had various issues with Lucid so wanted to try the beta version of maverick.

I have created separate partitions for Maverisk to install its root and home partitions but I don't want it to install grub as I am happy to continue using Karmic's grub which currently controls my boot up.

In previous versions at installatio there was an option not to have the bootloader installed but on Maverick this option is no longer available.

Do I just install the bootloader to the root partition of Maverick?

Please help as I do not want to screw up my current dual boot system but would like to try Maverick.

:-)

An advance trick is to save the current MBR then restore it after Maverick stomps on it and then update-grub using Karmic:
Find out what "/dev" your hard drive is is first (hda,sda,etc):
```
sudo fdisk -l

```
Save MBR+partition table:
```
sudo dd if=/dev/sda of=/mbrbackup.bin bs=512 count=1

```Restore MBR+partition table:

```
sudo dd if=/mbrbackup.bin of=/dev/sda bs=512 count=1

```

---

### Post by ktp on 2010-09-04
word of warning...you should be careful with dd command.  If you are not sure what the command will do, think twice before doing it on your "production" system.

---

### Post by ranch hand on 2010-09-04
Now that is cool.  Never heard of that.  I like it.  Thanks.

---

### Post by oldfred on 2010-09-04
If you use bs of 512 you are also copying the partition table. Which is ok if you make no changes to the partition table. Woe be to those who change partition table then restore old table.

bs=446 is just the MBR without the partition table.

---

### Post by jaycee23 on 2010-09-04
Out of interest what would happen if I installed the bootloader to sda7 (Maverick's root partition) instead of just sda?

---

### Post by ktp on 2010-09-04
this is why i was warning about dd command...one should be very careful with it or end up with unusable system.

If people want to know about MBR, following wiki is pretty good start:
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

Also good to know that grub and grub 2 use more the just MBR:
[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html)

---

### Post by dino99 on 2010-09-04
> **jaycee23 said:**
> Out of interest what would happen if I installed the bootloader to sda7 (Maverick's root partition) instead of just sda?

all my systems are installed like that: grub2 directly on the same ubuntu partition, and you know what: there is no complaint or sad effect, so im more quiet as it cant overwrite other bootloader(s) elsewhere. (i know that grub devs says to install into mbr but lbr is fine too)

---

### Post by VMC on 2010-09-04
> **oldfred said:**
> If you use bs of 512 you are also copying the partition table. Which is ok if you make no changes to the partition table. Woe be to those who change partition table then restore old table.

bs=446 is just the MBR without the partition table.

Why would you copy just the executable part of the MBR and leave off the partition table?

The OP stated he has already created his partitions for Maverick. Hence its now included in the partition table.

Once he has Maverick installed and his MBR restored he can use Karmic to update grub to now include Maverick.

That's why I stated its advance. The people that have replied here have obviously never used the method, only read about its perceived dire consequences.

---

### Post by kansasnoob on 2010-09-04
Keeping it simple:

Mavericks grub2 should find all of your OS's, so you'll be able to boot your Karmic.

Once you've booted into Karmic simply restore it's grub with:

```
sudo grub-install /dev/sd**[COLOR="Red"]X[/COLOR]**
```

Of course the **[COLOR="Red"]X[/COLOR]** will have to be replaced with the proper drive designation, and if you have only one internal drive it should be "a".

Some time ago I began a new "boot restore" post but I've been busy so it's not finished:

[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

When my house quits eating me and all of my money I'll hopefully be able to fix that :)

---

