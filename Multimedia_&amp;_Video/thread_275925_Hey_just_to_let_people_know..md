---
title: "Hey just to let people know."
date: 2006-10-12
forum: Multimedia &amp; Video
---

### Post by sktfeelsdapper on 2006-10-12
I think the codecs that are talked about in the "Customization guide" and how to install everything you need are infected with a virus. I'm doing a scan right now and that's the first thing that came up, so you guys might want to do a scan yourself. I'm probably going to have to delete the codecs and get the ones off the ubuntuguide.

Just a warning.:KS

---

### Post by frodon on 2006-10-12
lol, which Customization guide are you talking about and what make you think of a virus ?
BTW, there's no known existing virus for linux.

---

### Post by sktfeelsdapper on 2006-10-12
[http://www.ubuntuforums.org/showthread.php?t=186792](http://www.ubuntuforums.org/showthread.php?t=186792)

That quick customization guide.
The virus is w32majest.a or something along those lines. (For the win32codecs)

Unfortunetly it looks like nothing is safe.
I'm running Aegis virus scanner right now, and that's what I came up with. But I deleted it, so I can't provide proof. I'm just telling you that's what I came up with.

---

### Post by frodon on 2006-10-12
Ok, i understand what's the problem now, i will contact ubuntu_demon and tell him about it, thanks for reporting.
If you wish you can use the plf repository to install w32codecs, you can be confident with this well known repository :
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

or just :
```
wget -c http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.deb
sudo dpkg -i w32codecs_20060611-1plf1_i386.deb
```

---

### Post by PriceChild on 2006-10-12
I think that this is a false positive.

It has been reported before. One of the dll's that isn't actually needed because of ubuntu's functionality pops up on people's scanners from time to time.

I've scanned with ClamAV and not found anything.

---

### Post by ubuntu_demon on 2006-10-13
I will put in my guide that it's a false positive.

I'm wondering whether the PLF package also produces this false warning. Probably it does. But if it doesn't then I will change to it in my guide. Can someone check this for me ?

---

