---
title: "Installation of w32codecs fails"
date: 2006-07-31
forum: Multimedia &amp; Video
---

### Post by Martango on 2006-07-31
I try to install the w32codecs by following the guide on

[https://help.ubuntu.com/community/RestrictedFormats#w32codecs]("https://help.ubuntu.com/community/RestrictedFormats#w32codecs")

I think that the download is successful but the installation fails. This is what terminal returns:

```
:~$ wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
--20:22:57--  http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
           => `w32codecs_20060611-0.0_i386.deb'
Resolving www.debian-multimedia.org... 213.186.33.16
Connecting to www.debian-multimedia.org|213.186.33.16|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://www.debian.org [following]
--20:23:03--  http://www.debian.org/
           => `index.html'
Resolving www.debian.org... 194.109.137.218
Connecting to www.debian.org|194.109.137.218|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

:~$ sudo dpkg -i w32codecs_20060611-0.0_i386.deb
Password:
dpkg: error processing w32codecs_20060611-0.0_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 w32codecs_20060611-0.0_i386.deb
```

I'm not sure what's going wrong, any suggestions?

Martin

---

### Post by T700 on 2006-07-31
You might try installing them via Automatix (see my sig for link). It is fast, safe, easy, and automatic.

Paul

---

### Post by Martango on 2006-07-31
Thanks, but I would like to avoid Automatix if possible. It gave me some problems with missing panel links in my Danish installation of Dapper, and since I'm a newbe I hope I will learn a lot more by doing everything manual. I know that would not be possible without this forum, so thanks everyone for helping newbe's like me!

---

