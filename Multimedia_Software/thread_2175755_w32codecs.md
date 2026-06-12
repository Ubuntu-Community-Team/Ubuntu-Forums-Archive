---
title: "w32codecs"
date: 2013-09-20
forum: Multimedia Software
---

### Post by jmy2888 on 2013-09-20
Hello !

I have found that medibuntu has closed it's doors.  Where do i find w32codecs to install in 13.04 ?  Gooleing still gives the adding of medibuntu and getting them from there but that is no longer an option.  Searching the forums for w32codecs gives no results found.

Thanks in advance for any help.

---

### Post by jmy2888 on 2013-09-20
Never mind i found them.

---

### Post by ibjsb4 on 2013-09-20
Where?

---

### Post by mc4man on 2013-09-20
> **ibjsb4 said:**
> Where?

Well they come from [mplayerhq.hu]("http://www.mplayerhq.hu/MPlayer/releases/codecs/") so if one wanted to install as a .deb then they are always here - 
[http://www.deb-multimedia.org/dists/unstable/non-free/binary-i386/package/w32codecs](http://www.deb-multimedia.org/dists/unstable/non-free/binary-i386/package/w32codecs)

Or for a couple of extra or if on 64 bit the 3 rarely needed then run this in a terminal (copy & paste as 1 complete command
(slightly modded from Andrew.46's mplayer guide

```
sudo mkdir -p /usr/lib/codecs && \
if [ "$(uname -m)" = "x86_64" ]; then
 wget http://www.mplayerhq.hu/MPlayer/releases/codecs/essential-amd64-20071007.tar.bz2
 tar xjvf essential-amd64-20071007.tar.bz2
 sudo cp -v essential-amd64-20071007/* /usr/lib/codecs
else
 wget http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20110131.tar.bz2
 tar xjvf all-20110131.tar.bz2
 sudo cp -v all-20110131/* /usr/lib/codecs
fi
```

---

### Post by jmy2888 on 2013-09-20
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)

---

### Post by ibjsb4 on 2013-09-20
> **mc4man said:**
> Well they come from [mplayerhq.hu]("http://www.mplayerhq.hu/MPlayer/releases/codecs/") so if one wanted to install as a .deb then they are always here - 
[http://www.deb-multimedia.org/dists/unstable/non-free/binary-i386/package/w32codecs](http://www.deb-multimedia.org/dists/unstable/non-free/binary-i386/package/w32codecs)

Nice :) Thanks

---

