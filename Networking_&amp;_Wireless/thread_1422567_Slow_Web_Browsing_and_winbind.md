---
title: "Slow Web Browsing and winbind"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by bkadoctaj on 2010-03-05
Hi all,

I've been working with Ubuntu Karmic Koala 64-bit on my MacBook (also have Mac OS X Snow Leopard and Windows 7 Ultimate 64-bit on there) and I noticed that my Internet connection became extremely slow (to connect to websites, but not to download per se) after I followed the directions in this thread: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534).  Basically, I set up my fstab to automatically mount two samba shares on my LAN and had to install winbind (according to the directions).  It turns out that having winbind installed is directly linked with my slow Internet connection.  It doesn't matter whether I'm connected wirelessly or by wire, it takes about 10-15 seconds to load pages if they even load at all.

I had a hunch that winbind was behind all this trouble and removed it and guess what?  Instantly my Internet connect was working perfectly, just like after a fresh install.  I'm at school right now so I can't see what functionality I've lost in terms of my samba share set up at the moment, but I'm fine mounting the shares manually just so I can have my Internet working like it should be.

Anyone else notice this?  Can anyone else verify that this is exclusively a Karmic (maybe 64-bit) issue?

bkadoctaj

EDIT:  It appears that removing winbind is not necessary to solve this issue.  The real culprit (for whatever weird reason) is automounting shares by netbios name in /etc/fstab.  By automounting using the static IP of the local computer I was able to surf the Internet without any slow page-loading.

---

### Post by jonkirian on 2010-03-24
Thanks for the fix / workaround!

---

### Post by bkadoctaj on 2010-03-24
Yeah man.  It was a frustrating situation, but all the options are somewhere in Ubuntu.  You just have to pinpoint where.

---

### Post by capscrew on 2010-03-24
> **bkadoctaj said:**
> Yeah man.  It was a frustrating situation, but all the options are somewhere in Ubuntu.  You just have to pinpoint where.

The answer is; The slowdown was due to the lack of name resolution.  You did not have name resolution set up correctly for the local hosts to talk to each other by name (either hostname or netbios name).

Winbind has nothing to do with name resolution.  DNS resolves hostnames and WINS (or netbios helper routines) resolve COMPUTER names.

---

