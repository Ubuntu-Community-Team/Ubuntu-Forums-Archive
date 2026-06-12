---
title: "problem with online media"
date: 2006-11-15
forum: Multimedia &amp; Video
---

### Post by toosweetnitemare on 2006-11-15
I am trying to watch some videos online, but they specifically are called "This is a Windows Media Video." when i try and run then it says i need a plug in so i try to install that and it says no plug in found. any ideas on how i can get that media running? 
](*,)

---

### Post by Jim March on 2006-11-15
It would help if you linked to them so we could try them!  You also don't say whether you're on Dapper or Edgy, or your video card type/computer type.

If you haven't done it yet, try the Automatix driver/codec updates:

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

---

### Post by toosweetnitemare on 2006-11-15
im using mplayer. i have Dapper and i run a lattitude d600 all stock. also but reinstalling the mplayer firefox plugin i have sound now but no picture. do you know what other plugins cover video on firefox? i was thinking of uninstalling them and seeing if mplayer can handle the whole load. what is automatix?

---

### Post by Jim March on 2006-11-15
Automatix is a tool for installing all that "eye candy" stuff for video, flash, etc.  Covers a lot of other utilities too.  Try it :).

---

### Post by pete on 2006-11-15
I was able to resolve the "sound but no video" problem with the mplayer plugin using the instructions from [the Restricted Formats page on the wiki]("https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5").

Specifically:

> wget -c [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb)
sudo dpkg -i w32codecs_20061022-0.0_i386.deb

---

### Post by toosweetnitemare on 2006-11-15
i recieved some errors Pete
> 
master@master-laptop:~$ wget -c [http://www.debian-multimedia.org/poo...2-0.0_i386.deb](http://www.debian-multimedia.org/poo...2-0.0_i386.deb)
--14:02:21--  [http://www.debian-multimedia.org/poo...2-0.0_i386.deb](http://www.debian-multimedia.org/poo...2-0.0_i386.deb)
           => `poo...2-0.0_i386.deb'
Resolving [www.debian-multimedia.org](www.debian-multimedia.org)... 213.186.33.16
Connecting to www.debian-multimedia.org|213.186.33.16|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/poo...2-0.0_i386.deb](http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/poo...2-0.0_i386.deb) [following]
--14:02:21--  [http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/poo...2-0.0_i386.deb](http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/poo...2-0.0_i386.deb)
           => `poo...2-0.0_i386.deb'
Resolving ftp.sunet.se... 194.71.11.70, 2001:6b0:19::64
Connecting to ftp.sunet.se|194.71.11.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
14:02:22 ERROR 404: Not Found.

master@master-laptop:~$ sudo dpkg -i w32codecs_20061022-0.0_i386.deb
dpkg: error processing w32codecs_20061022-0.0_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 w32codecs_20061022-0.0_i386.deb
master@master-laptop:~$

---

### Post by toosweetnitemare on 2006-11-15
> **Jim March said:**
> Automatix is a tool for installing all that "eye candy" stuff for video, flash, etc.  Covers a lot of other utilities too.  Try it :).

also i am having problems installing automatix, Jim. I think a combo of both your suggestions will work nicely. thank you both.

---

### Post by pete on 2006-11-15
D'oh!

My bad, toosweetnitemare...  looks like when I copied and pasted those commands into my response, it truncated the URL, which is why your wget is returning a 404.

Go to the wiki page I linked to.  The full URL for the wget is listed there.

---

### Post by toosweetnitemare on 2006-11-15
haha that makes sense now

---

### Post by toosweetnitemare on 2006-11-15
Pete your the man!! that worked. Thanks for your help Jim but automatix is giving me a hassel so im going to drop it for now. Thanks all

---

