---
title: "No Space in samba mount"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by skintythe1andonly on 2010-03-14
Hi

My wireless router has a USB port that I can plug in hard drives which can then be mounted.

If I mount the drive through Nautilus, it mounts fine but if I try to copy anything to the drive through nautilus I get a pop-up window saying that there was "an invalid argument". I have no idea what this means

What is more strange is if I try to mount the drive, using something like
```
sudo mount -t cifs //netbiosname/sharename /media/sharename -o guest,iocharset=utf8
```
it mounts ok and I can read everything on the drive. The drive is a 320GB Iomega drive. If I try to copy anything to it, it claims that there is only 29.4Mb left. If I check the properties I get the following
[ATTACH]150137[/ATTACH]

note it states the capacity is 30Mb  but the contents totals much more than that. I am not so sure of the options, can anybody help me out?

---

