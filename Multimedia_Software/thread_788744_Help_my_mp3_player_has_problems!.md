---
title: "Help my mp3 player has problems!"
date: 2008-05-10
forum: Multimedia Software
---

### Post by helpineed on 2008-05-10
as the title suggests my mp3 player does not work on ubuntu. when i want to add songs to it it just tells me i have no permission. i have tried changing the permissions

---

### Post by Ripfox on 2008-05-10
what model

---

### Post by Ripfox on 2008-05-10
Check permissions and ownership with:
```
ls -l
```

You can change the permissions of the entire tree with:
```
sudo chmod -R 755 /media/Dati/*
```

---

### Post by helpineed on 2008-05-16
sorry for the delay my internet crashed for a week ](*,) .Its an ipod shuffle and for every file inside the player it goes
```
chmod: changing permissions of `/media/disk/song.mp3': Read-only file system

```
help!.please

---

### Post by BandD on 2008-05-16
I had a similar issue with a built-in memory card reader.  Everytime I would put the memory card in and try to delete, move, or add files, it would tell me I didn't have permission.  I tried changing the persion of the /media/... mount point, but to no avail.

Then I opend up Gparted (you can install it through synaptic, and there'll be a launcher in System-->Administration) and saw that the 'real' location of the device was actually /dev/... something.  So I change the permission of that location and all seemed to work!

It's worth a shot.

---

