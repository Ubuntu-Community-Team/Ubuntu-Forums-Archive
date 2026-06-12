---
title: "DLink wireless card - installation"
date: 2006-05-05
forum: Networking &amp; Wireless
---

### Post by leandro_tami on 2006-05-05
I've got a PCI DWL-G510 DLink WiFi card and it seems I just can't get it working with Ubuntu 5.10. The main problem is that I'm a complete Linux newbie.
My hardware is quite cheap: an PC-Chips motherboard with a 333Mhz Celeron micro. It hasn't got any floppy drive or USB interface. Therefore, if I need to download something I'll have to do it using other computer and then burning it to a CD.
My goal is creating a http/ftp server with it.

---

### Post by monomaniacpat on 2006-05-05
[http://linux-wless.passys.nl/query_part.php?brandname=D-Link&zoek=Show](http://linux-wless.passys.nl/query_part.php?brandname=D-Link&zoek=Show)

A quick perusal suggests your card may be supported. Download the file, and read the INSTALL file - it should tell you what to do. PM me or post here if you get stuck.

---

### Post by ArchStanton on 2006-05-20
I'm trying to get the same card running. I followed the link to this page . . .

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Frestricted%2Fl%2Flinux-restricted-modules-2.6.12%2Flinux-restricted-modules-2.6.12-10-386_2.6.12.4-11.1_i386.deb&md5sum=3e9561e07d060c179f6d17810cb8ca28&arch=i386&type=security](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Frestricted%2Fl%2Flinux-restricted-modules-2.6.12%2Flinux-restricted-modules-2.6.12-10-386_2.6.12.4-11.1_i386.deb&md5sum=3e9561e07d060c179f6d17810cb8ca28&arch=i386&type=security)

I downloaded the file (linux-restricted-modules-2.6.12-10-386_2.6.12.4-11.1_i386.deb) to my USB drive and took it over to the machine running Breezy. I can't figure out what to do with the file now. Any help?

---

### Post by ArchStanton on 2006-05-20
Well, I guess that package is already installed. So the DLink DWL-G510 doesn't work despite what that list says.

---

### Post by ArchStanton on 2006-05-21
On further inspection, it is only the Dlink DWL-G510 Revsion B that works. Revision A, which I have, doesn't.

---

### Post by avirnig on 2006-05-21
ok so since you found out that certain revisions of cards may not work with linux drivers you have another option, but it is a bit harder to do.

try ndiswrapper. Ndiswrapper is a package of software that basically wraps the windows xp driver in a software "shell" that lets linux see it as a native driver.

people's first reaction to this is "oh, but that has to be slower" and in some rare cases it is, however it usually works at the same speed as a windows box would.

i wont go into specifics on how to use ndiswrapper as there are PLENTY of guides on the net, but i will tell you that you can probably get your card auto-detected in dapper drake, if you cant, then you will have to use ndiswrapper.

---

