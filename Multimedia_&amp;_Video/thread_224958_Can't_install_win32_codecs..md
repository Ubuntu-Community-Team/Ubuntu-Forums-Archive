---
title: "Can't install win32 codecs."
date: 2006-07-28
forum: Multimedia &amp; Video
---

### Post by sdmike on 2006-07-28
So I tried to install aud dvd codecs in automatix for Dapper but it was having trouble installing it and I read about other people having problems to. So I tried downloading the codecs manually but when I get to this part:

root@jack-desktop:~# wget -c [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb)
--17:28:11--  [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb)
           => `w32codecs_20060611-0.0_i386.deb'
Resolving [www.debian-multimedia.org](www.debian-multimedia.org)... 213.186.33.16
Connecting to www.debian-multimedia.org|213.186.33.16|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.debian.org](http://www.debian.org) [following]
--17:28:12--  [http://www.debian.org/](http://www.debian.org/)
           => `index.html'
Resolving [www.debian.org](www.debian.org)... 194.109.137.218
Connecting to www.debian.org|194.109.137.218|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 15,443 (15K), 969 remaining [text/html]

100%[++++++++++++++++++++++++++++++++++==>] 15,443        --.--K/s

17:28:12 (57.76 MB/s) - `index.html' saved [15443/15443]

root@jack-desktop:~# sudo dpkg -i w32codecs_20060611-0.0_i386.deb
dpkg: error processing w32codecs_20060611-0.0_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 w32codecs_20060611-0.0_i386.deb
root@jack-desktop:~# sudo apt-get install mpg321 vorbis-tools
Reading package lists... Done
Building dependency tree... Done
mpg321 is already the newest version.
vorbis-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@jack-desktop:~# sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree... Done
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@jack-desktop:~# sudo apt-get install libxine-extracodecs
Reading package lists... Done
Building dependency tree... Done
libxine-extracodecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@jack-desktop:~# sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
Reading package lists... Done
Building dependency tree... Done
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@jack-desktop:~# wget -c [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb)
--17:30:54--  [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb)
           => `w32codecs_20060611-0.0_i386.deb'
Resolving [www.debian-multimedia.org](www.debian-multimedia.org)... 213.186.33.16
Connecting to www.debian-multimedia.org|213.186.33.16|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.debian.org](http://www.debian.org) [following]
--17:30:55--  [http://www.debian.org/](http://www.debian.org/)
           => `index.html'
Resolving [www.debian.org](www.debian.org)... 194.109.137.218
Connecting to www.debian.org|194.109.137.218|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

root@jack-desktop:~# sudo dpkg -i w32codecs_20060611-0.0_i386.deb
dpkg: error processing w32codecs_20060611-0.0_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 w32codecs_20060611-0.0_i386.deb
root@jack-desktop:~#

Can somebody please tell me what I should do?

---

### Post by wieman01 on 2006-07-28
Well, yes. Instead of downloading the *.dev file you are merely pulling an "index.html" file. So the subsequent error message tells you exacly that, the system has not found the *.deb file on your drive.


I would do the following... Download the *.deb file using your browser. Simply click on the link below... Then continue with the second part (dpkg -i...). 

That should do.

[http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb]("http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb")

Another useful link if you want to turn your computer into a media center in just three steps:

[http://www.ehomeupgrade.com/entry/2663/how-to_get_full]("http://www.ehomeupgrade.com/entry/2663/how-to_get_full")

---

### Post by arnieboy on 2006-07-29
its a known bug in version 6.4-2 of automatix. will be fixed in the next version.

---

### Post by sdmike on 2006-07-29
So I did all that and totem is playing my videos but I wanted mplayer to play. Now the video quality is really bad it looks all pixalared and the color is way off like viewing a movie with the negative color.

---

### Post by sdmike on 2006-07-29
Also just to add. This is the same computer I had kubuntu on before and mplayer worked perfectly. But now I switched it ubuntu and did the video stuff and now I'm stuck.

---

