---
title: "making iso from dvd with terminal"
date: 2007-10-01
forum: Multimedia &amp; Video
---

### Post by almancora on 2007-10-01
Hi all,

I'm new to ubuntu. I wanted to try out something in the terminal On a site i've read that you could make iso's from dvd's with the terminal. 
this is what i got:

ruben@ruben-laptop:/dev$ sudo dd if=/dev/cdrom of=fourtetdvd.iso
Password:
dd: writing to `fourtetdvd.iso': No space left on device
1025001+0 records in
1025000+0 records out
524800000 bytes (525 MB) copied, 199,044 seconds, 2,6 MB/s

(my hard disk isn't full at all)

greetz

---

### Post by disraeli on 2007-10-01
It seems you're in the dev directory, try doing the same operation by changing directory to your home first.

---

### Post by vanadium on 2007-10-01
The command looks OK, but the error message suggests that there is indeed a disk space problem. So to check twice, check the output pf the command

df

which among other things will list your hard drive and the free space. Another thing to check is that your current directory indeed is located on the drive with enough free space. 

pwd

A DVD image can require 4 GB and more, so you should have plenty of free space.

---

