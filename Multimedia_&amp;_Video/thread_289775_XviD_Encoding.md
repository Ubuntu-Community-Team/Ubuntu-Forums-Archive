---
title: "XviD Encoding"
date: 2006-10-31
forum: Multimedia &amp; Video
---

### Post by RaVel on 2006-10-31
Hi :)
I did XviD encoding many times in Windows (using mainly VirtualDub) but never in Linux. Since I have 32bit Windows and 64bit Ubuntu installed I would prefer to use 64bit environemnt (heard it's faster in encoding). But I have no idea what packages do I need to do the encoding. Since I want to have audio in mp3 I think I will also need something for this.
I have a standard Ubuntu Dapper installation (I've only installed ATi driver).
Please, help.

---

### Post by ahaslam on 2006-10-31
I've used acidrip to rip a DVD to xvid/mp3. It worked quite nicely & it was faster than expected.

Homepage: [http://untrepid.com/acidrip/](http://untrepid.com/acidrip/)

Unfortunately the GUI [was/i]sn't perfect. It's been a while since I've used it. From what I remember a line of the output needs to be modified & pasted in a terminal. I'll look into this for you & point you in the right direction.

Tony.

EDIT: here it is: [http://ubuntuforums.org/showthread.php?t=156898&highlight=acidrip](http://ubuntuforums.org/showthread.php?t=156898&highlight=acidrip)

It's just a '**:**' that needs to be removed from the output, it's quite simple ;)

---

### Post by Cynical on 2006-10-31
A good VirtualDub replacement in linux is avidemux. (screenshot below) 

Here is a link to the [package](http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Fmultiverse%2Fa%2Favidemux%2Favidemux_2.1.2-0.0ubuntu3_amd64.deb&md5sum=5ef1d4db2a78d5f1abab1c2011f4d45a&arch=amd64&type=main)

I'd also recommend the x264 codec over xvid, it lowers the file size substantially.

---

### Post by garretwp on 2006-11-01
Does anyone have any sync issues with avidemux? I can not get the sync to match when I try to convert vob files over to xvid.

- Garrett

---

### Post by zwaardmeester on 2006-11-08
For dvd ripping to xvid see [http://www.exit1.org/dvdrip/](http://www.exit1.org/dvdrip/)

---

