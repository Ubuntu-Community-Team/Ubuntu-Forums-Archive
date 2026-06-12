---
title: "Ubu do not mount any partitions after 10.10 -&gt; 11.04 upgrade."
date: 2011-02-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by przemo_li on 2011-02-05
I've upgraded to 11.04 alpha 2

After booting Ubuntu says that can not mount / partition or any other.

Manuall investigation showed that /dev/sda6 is in use (may / partition), unmounting works, but mtab still shows it as mounted.

So mount /dev/sda6 / -t ext4
gives:

/dev/sda6 is mounted or busy
according to mtab /dev/sda6 is mounted as /

unmount -fv /
unmounted succesfully

but another mount gives the same answer as first
:confused::confused::confused:

any idea?

---

### Post by coffeecat on 2011-02-05
There's something not right here:

> **przemo_li said:**
> unmount -fv /
unmounted succesfully

First - the command is umount, not unmount. Second, you can't unmount your / (root) partition. Third, if you unmount a mounted partition (not your root) with 'sudo umount -fv <mountpoint>' you get the message, '<device> umounted', not 'umounted successfully'.

My root partition is on sda11. First:

```
$ sudo mount /dev/sda11 / -t ext4
mount: /dev/sda11 already mounted or / busy
mount: according to mtab, /dev/sda11 is already mounted on /
```... which is exactly what I would expect. And...

```
$ sudo umount -fv /
umount2: Device or resource busy
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount2: Device or resource busy
```... which is also what I would expect. If you are relly getting 'umounted successfully', then something is very wrong.

Post the output of:

```
sudo fdisk -lu
```...and...

```
sudo umount -fv /
```Copy and paste the output - we need to see exactly what you are getting. please use code tags for legibility.

I'll ask a mod to move this - you've posted in the wrong forum.

---

### Post by howefield on 2011-02-05
Thread moved to Natty Narwhal Testing and Discussion forum.

---

### Post by przemo_li on 2011-02-05
Sorry for mistyping.

Commands where issued as root, on root account.

Ubuntu when can't mount any partition during boot, can skip it (S), or go to command line (M) as root.

And thats mean no "copy and paste" but "write it down on paper then rewrite here!"

To my best knowledge kernel (or init process ?) when mounting partitions according to fstab, can't mount /
Then I jump into cli, and still cant mount /dev/sda6 because it is used as /. After umoutning it succesfully, mtab still contain info about mounted / !!! This is bug (or consequences of real one).

---

### Post by coffeecat on 2011-02-05
> **przemo_li said:**
> Ubuntu when can't mount any partition during boot, can skip it (S), or go to command line (M) as root.

OK, I follow you now. You are getting errors **during** the boot process. This...

> **przemo_li said:**
> After booting Ubuntu says that can not mount / partition or any other.

...sounded as though you were trying to mount the root partition **after** you had booted.

Question: despite the errors on bootup, can you get to the desktop? Perhaps we need to look at your fstab and other details of your setup. The best way would be to boot up the live CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the RESULTS.txt file. **Please** enclose the output in [noparse]```
 and 
```[/noparse] tags for legibility.

---

