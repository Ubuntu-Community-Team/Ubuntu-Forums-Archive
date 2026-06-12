---
title: "can't install from disc"
date: 2010-07-26
forum: Multimedia Software
---

### Post by campusgray on 2010-07-26
Hi all, newbie to installing programs. I'm trying to install my camera software through cd/rom. When clicking install.exe i get the following error.

Archive:  /media/CanonDC300W/setup.exe 
[/media/CanonDC300W/setup.exe] 
  End-of-central-directory signature not found.  Either this file is not 
  a zipfile, or it constitutes one disk of a multi-part archive.  In the 
  latter case the central directory and zipfile comment will be found on 
  the last disk(s) of this archive. 
zipinfo:  cannot find zipfile directory in one of /media/CanonDC300W/setup.exe or 
          /media/CanonDC300W/setup.exe.zip, and cannot find /media/CanonDC300W/setup.exe.ZIP, period.

---

### Post by cj.surrusco on 2010-07-26
The software that you are trying to install is Windows software. The only way you can install that is with a program like Wine. It is available in the repositories, so just input the following into a terminal:
```
sudo apt-get install wine
```

---

### Post by themusicalduck on 2010-07-26
After installing wine you need to right click on the exe file, go to Properties. Then check that the Open With tab is set to wine.

Also, if it's running off a CD and you are on 10.04, you may need to copy the files off the CD onto the Desktop (or somewhere on the harddrive). Then click on the exe file, go to Properties again, check the Permissions tab and check the Allow executing file as a program box.

Lastly, I'd recommend installing wine1.2 rather than wine, because it is more up to date and more likely to work.

Run ```
sudo apt-get install wine1.2
``` in a terminal. (Applications > Accessories > Terminal)

Also, it's worthwhile looking the software up at [http://appdb.winehq.org/](http://appdb.winehq.org/) to see if it's likely to work.

---

### Post by campusgray on 2010-07-27
Thanks for the help. I found another program which seems to work just as well as the software on the disc, but will keep in mind the wine program. I found....


.sudo apt-get install gphoto2 gtkam gtkam-gimp


thanks for the quick reply. The more I use this open source, it boggles my mind why windows is so popular. Ubuntu for life now

---

### Post by cj.surrusco on 2010-07-27
> **themusicalduck said:**
> 
Lastly, I'd recommend installing wine1.2 rather than wine, because it is more up to date and more likely to work.

Run ```
sudo apt-get install wine1.2
``` in a terminal. (Applications > Accessories > Terminal)

Also, it's worthwhile looking the software up at [http://appdb.winehq.org/](http://appdb.winehq.org/) to see if it's likely to work.

Correct me if I am wrong, but the 'wine' package installs the newest version, which is currently wine1.2 ;)

---

### Post by themusicalduck on 2010-07-27
> **cj.surrusco said:**
> Correct me if I am wrong, but the 'wine' package installs the newest version, which is currently wine1.2 ;)

Oh, oops, yeah it looks like it. :)

I just always see people using that command as the new version, and  "wine" as version 1.0. Maybe they changed it at some point.

---

