---
title: "How many of you are able to play commercial DVDs"
date: 2008-05-27
forum: Multimedia Software
---

### Post by masonfoley on 2008-05-27
Trying to get a feel for how many folks are able to play commercial DVDs with the latest kernel.  (Ubuntu 2.6.24-17.31-generic)  For over a week now, I've been all over the 'Net and found well over 35 threads where people have had one issue or another.  Some, though not as many as you would think, were solved with the typical medibuntu codec repo or simply acquiring libdvdcss2.

A significant amount of other folks on the other hand ([including myself]("http://ubuntuforums.org/showthread.php?t=802980")), despite all attempts at troubleshooting are not able to get encrypted DVDs to play.

So if you have done the usual prescription of installing libdvdcss2 and/or installing codecs and libraries from medibuntu, answer No, I can't.  Otherwise, say Yes.

Please don't answer "No, I can't" if you haven't performed the requisite steps required post-install of your Ubuntu distro (i.e. libdvdcss2, libdvdnav, libdvdread installations).

And Sweet Buddha...if you were able to overcome this issue, please post what you think finally got the gear unstuck.

Cheers

---

### Post by Ballistixx on 2008-05-27
I couldn't until I typed in to a terminal

sudo apt-get install build-essential

then type

sudo /usr/share/doc/libdvdread3/install-css.sh

64 bit users need a diff. code.


Cheers,
Jason

---

### Post by justineve on 2008-05-27
Hi, Masonfoley
Sorry friend.
I have never done the usual prescription of installing libdvdcss2 
so I don't have any idea of that. Sorry. 
But all the best to get right suggestion.

---

### Post by Vivaldi Gloria on 2008-05-27
After

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

it works.

---

### Post by Rinzwind on 2008-05-27
I can.

Just needed to do the normal extras after Hardy install.

---

### Post by Monicker on 2008-05-27
> **Vivaldi Gloria said:**
> After

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

it works.

The above worked for me too.

---

### Post by phoenix_abhi on 2008-05-27
code:

sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 build-essential debhelper fakeroot

after the above

sudo /usr/share/doc/libdvdread3/examples/install-css.sh


 working fine with VLC

---

