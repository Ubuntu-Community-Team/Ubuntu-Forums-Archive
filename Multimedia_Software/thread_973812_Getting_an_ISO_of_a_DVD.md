---
title: "Getting an ISO of a DVD"
date: 2008-11-07
forum: Multimedia Software
---

### Post by RMSe17 on 2008-11-07
Using Ubunti 8.04.1 x86_ai64

I am trying to get an ISO from a Bootable Data DVD.  My problem is that K3B and Brasero both see it as a 688MB CD when I try to use them for a Duplicate to Image...  they make an iso, but it is 688MB, and thus can not possibly be the whole DVD.

Any suggestions?

---

### Post by Open-SuSe-A-Me on 2008-11-07
hmmm...i guess the first thing you should do is look at the underside of the disc and check how much of the disc is written upon (would be a slightly different color) and if it is a very small amount than it could be a CD ISO image that was put onto a DVD.

if that doesnt help open the disc's folder with nautilus and right click properties and see what that says.

---

### Post by RMSe17 on 2008-11-07
Definitely not.  There are 4 650MB folders on the DVD

---

### Post by RMSe17 on 2008-11-10
any other suggestions?

---

### Post by mc4man on 2008-11-10
If you wanted to install wine and put a little time into setting up and learning Imgburn then you could forget about having any problems in terms of iso creation, burning, reading of non encrypted disks and compatibility with other Os's.

For a linux only you could try to dd the disk

```
dd if=/dev/scd[COLOR="Red"]0[/COLOR] of=dvd.iso
```
(adjust red to match your drive if different

Or install dvdisaster and use that to 'read' the disk. (create an iso copy)
Dvdisaster is better if the disk condition is a factor, dd can fail if it encounters read errors

Example of slightly damaged outer area on a dvd data disk. In this case a successful read was done in one pass (no red blocks), but it did require some read retries.
 If the first run had produced unreadable sectors then dvdisaster can be re run multiple times. In that case it will only attempt re reading the skipped (red block) areas, not redoing the whole read from scratch.
see screen

---

