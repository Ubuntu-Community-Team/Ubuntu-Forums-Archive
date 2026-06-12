---
title: "Grip Ripping/Encoding"
date: 2007-08-22
forum: Multimedia Production
---

### Post by MemoryDump on 2007-08-22
I have Grip setup, however it won't detect/load any discs I put in my CDROM drive.

I have 2 DVD drives. /media/cdrom0 and /media/cdrom1
I've tried changing the config settings in Grip to use the proper drive, however it's not loading/reading. 
For whatever reason 1 of the drives isn't readable at all my system under Ubuntu.. but it works under Windows. But I have 1 drive that work ("cdrom0" I think) and I can play music cd's from it using a media player.

---

### Post by Amazona aestiva on 2007-08-22
Ripping is in my signature.

---

### Post by MemoryDump on 2007-08-22
> **Amazona aestiva said:**
> Ripping is in my signature.

you lost me :confused:

---

### Post by Amazona aestiva on 2007-08-23
There is a link in my signature!

---

### Post by stmiller on 2007-08-23
Try /dev/cdrom

or /mnt/cdrom

and other combinations in grip.

---

### Post by MemoryDump on 2007-08-23
> **Amazona aestiva said:**
> There is a link in my signature!
I followed that link, however I didn't see anything pertaining to my problem. Only how to rip/make dvds.

---

### Post by Amazona aestiva on 2007-08-24
Now I understand... sorry for mistake.
So one of your drives can't mount a disc which is playable under Windows.
You should get an error message when try to mount like this:
"Invalid mount option when attempting to mount the volume 'disc name'"
For this here is a solution:

Create a backup for /etc/fstab

Open terminal and type:
```
gksudo nautilus
```
In that window you have permission to everything!(be careful)

Then open it (/etc/fstab) and find the lines starting with:
/dev/hdc
/dev/hdd

Modify the lines to this:
```
/dev/hda	/media/cdrom0	auto	users,noauto	0	0
/dev/hdb	/media/cdrom1	auto	users,noauto	0	0
```

If something went worse use the backup!

---

### Post by MemoryDump on 2007-08-25
in my fstab I currently have this:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
```
wouldn't that be right already? :confused:

---

### Post by Amazona aestiva on 2007-08-25
It should be right!

I had a problem like yours and this helped me... I don't know what's wrong with Your computer. Sorry...

---

### Post by eeried on 2007-11-12
New with Gutsy, it seems: grip wants /dev/scdx (replace x by 0, 1 etc)

With feisty, /dev/cdrom worked fine for me.

K3b reads  /dev/scd0 on its own without any config.

Why don't we have /dev/hdc or /dev/cdrom anymore? Still I have /dev/hdc in my old fstab file (I upgrade from Xubuntu Feisty to Gutsy online.

---

