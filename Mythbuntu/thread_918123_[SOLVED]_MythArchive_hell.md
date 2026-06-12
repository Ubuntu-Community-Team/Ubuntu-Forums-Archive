---
title: "[SOLVED] MythArchive hell"
date: 2008-09-12
forum: Mythbuntu
---

### Post by ian dobson on 2008-09-12
Hi,

Does anyone have MythArchive working?

Hardware setup:-
Backend server with 4Tb harddisk space
Running 64bit Ubuntu with the MythTV package installed and working.
Samba file sharing

Frontend
Core2Duo 1.8GHz
1Gb RAM
SATA DVD-Burner
Mythbuntu 32bit also working

I can run MythArchive and it creates a DVD that I can play back on the frontend but when I try and play it on a DVD-Player or try and look it on a windows PC the player doesn't recognise the DVD. On windows I don't see any files or directories (VIDEO.TS/AUDIO.TS).

I've got the feeling that the problem is the format (NOT ISO-9xxx) that MythArchive/growisofs uses for the DVD.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-09-13
anyone?

---

### Post by mrand on 2008-09-13
I haven't gotten around to installing a DVD drive in my Myth box, so I have MythArchive generate an .iso and then I burn that on a windows machine.  You might try that and see if it works.

I may try installing the drive, but it certainly won't be today, and I may not be able to get to it for a number of days.
[INDENT] Marc[/INDENT]

---

### Post by agamotto on 2008-09-18
I gave up on this completely, as Mytharchive hasn't worked for me since 7.10.  I finally just broke down and purchased a bundle of 2gb usb sticks for a cheap price and hand them out with the mpg files if someone wants a recording.

---

### Post by Nikas on 2008-09-18
Try another version of growisofs.
I had the same problem.

This solved my problem:
```
wget http://ftp.se.debian.org/debian/pool/main/c/cdrkit/genisoimage_1.1.8-1+b1_i386.deb
sudo dpkg -i genisoimage_1.1.8-1+b1_i386.deb
```

If you need the 64bit-package, look here:
[http://ftp.se.debian.org/debian/pool/main/c/cdrkit/](http://ftp.se.debian.org/debian/pool/main/c/cdrkit/)

---

### Post by ian dobson on 2008-09-20
Hi Nikas,

Thanks that worked for me, I just installed genisoimage_1.1.8-1+b1_i386 and it worked.

Regards
Ian Dobson

---

### Post by axelsvag on 2008-09-21
If it is so easy, why is not an update to mythbuntu released. Or is it something more in the problem?

---

### Post by mrand on 2008-09-22
> **axelsvag said:**
> If it is so easy, why is not an update to mythbuntu released. Or is it something more in the problem?

Mythbuntu 8.04 has 1.1.6 because it is based upon Hardy, and no-one has backported 1.1.8 to Hardy.

Intrepid (8.10) will have genisoimage 1.1.8, so Mythbuntu 8.10 will have this fixed.

---

### Post by klc5555 on 2008-10-01
> **Nikas said:**
> Try another version of growisofs.
I had the same problem.

This solved my problem:
```
wget http://ftp.se.debian.org/debian/pool/main/c/cdrkit/genisoimage_1.1.8-1+b1_i386.deb
sudo dpkg -i genisoimage_1.1.8-1+b1_i386.deb
```

If you need the 64bit-package, look here:
[http://ftp.se.debian.org/debian/pool/main/c/cdrkit/](http://ftp.se.debian.org/debian/pool/main/c/cdrkit/)


It seems that the wonky version of growisofs from genisoimage 1.1.6 in Hardy was also cheerfully provided in the 0.21 Mytharchive backport for Gutsy.

In the case of Gutsy systems running the 0.21 backport, upgrading genisoimage to  1.1.8 as described above fails the dependency check for libc6 2.7 and above; Gutsy uses libc6 2.6.

This is a problem that would take about 5 minutes for me to correct on one of my Slackware machines, either by upgrading just libc6 or downgrading just DVD-r/w tools, but I don't know the correct Ubuntu/Debian approach to use. 

Is there a simple method for backing down just genisoimage to some earlier iteration without affecting the rest of the Mytharchive installation?

growisofs from the 7.10 release installation CD is the last known good version (prior to genisoimage 1.1.8 ), but the Mythbuntu package managers will not allow me to mess with any of the DVD-writing tools without also uninstalling Mytharchive 0.21, K3b, et al. 

I'm sure the methodology here must be simple, I just don't know what it is. :confused:

---

