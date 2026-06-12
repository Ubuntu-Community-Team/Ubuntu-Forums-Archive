---
title: "Can't play MPG or WMV"
date: 2006-08-25
forum: Multimedia &amp; Video
---

### Post by mpcsm on 2006-08-25
I'm a newbie so please excuse me.

I can't play MPEG, MPG, AVI, WMV formats in Totem

I read about the restricted file format and understand why.

I read other posts and someone claims that the following command lines will install th enecessary codec and all will be ok

wget -c [http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb](http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb)
sudo dpkg -i w32codecs_20060611-1plf1_i386.deb

Well I did and still can't play the files. I keep getting the message that I do not have a decoder installed to handle this file

Any help would be appreciated....remember I'm a newbie

---

### Post by Greycloak on 2006-08-25
I used automatix to download the codecs.  Installation and instructions are here:

[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix)

---

### Post by mpcsm on 2006-08-25
Worked like a charm...Thank you so much

---

### Post by apc15x on 2006-08-25
I too can't play MPG ro WMN but when I go into Automatix it is fine until I get to the password but when I type my password the cursor dosen't move. Am I doing something wrong?  Any help would be appreciated and thank in advance.

apc15x

---

### Post by CorruptKode on 2006-08-26
It's not suppose to just type in your password and press enter should work.

---

### Post by true_friend on 2006-08-26
u may got some problem with automatix. u can manually install the packages named [here]("https://help.ubuntu.com/community/RestrictedFormats#w32codecs")
read this page carefully u will get a lot of knowledge in this regard. and there are not any commands involved here also GUI work with mouse clicks.
Regards
True_Friend

---

### Post by bluntu on 2006-08-27
I experienced this problem too and again, I'm one of those people who likes simple solution to a problem so here it is if you are having difficulty playing WMV files with MPlayer.

Step 1:
Download the codec: Go here: [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)
and look for "Essential Codecs Package" which is at the bottom of the screen.

Pick a HTTP/FTP location and download it onto  your desktop.

Step 2:
Extract all the files inside that .tar into a **folder** and give it a name that you can remember and easier to type.

Step 2:
Open up the terminal and go right into that **folder**.

Step 3:
$ sudo mkdir /usr/lib/win32
$ sudo cp * /usr/lib/win32


Step 4: done...


The idea is to copy all the files into /usr/lib/win32
If you don't have a folder called win32 then make one. Mine doesn't have it so that was what I did and it works.

---

