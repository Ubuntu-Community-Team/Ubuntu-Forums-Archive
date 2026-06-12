---
title: "Where are avisynth, libnut, librtmp, libvpx in Ubuntu 10.04?"
date: 2010-07-20
forum: Multimedia Software
---

### Post by jiapei100 on 2010-07-20
Hi, all:

I'm currently trying to compile a full version of ffmpeg 0.6 .
However, some of the packages are not afforded by Ubuntu 10.04,
including avisynth, libnut, librtmp, libvpx.

It seems avisynth is only for Windows.
But, it seems libnut, librtmp and libvpx have been afforded by Debian. (not quite sure).
I'm wondering if Ubuntu 10.04 repository will also afford such package in future?

Best Regards
JIA

---

### Post by rubylaser on 2010-07-20
If you want to use those packages, you're going to need to compile them, here are some nice directions to get it working for you.
[http://ubuntuforums.org/showpost.php?p=9114176&postcount=967]("http://ubuntuforums.org/showpost.php?p=9114176&postcount=967")

---

### Post by jiapei100 on 2010-07-20
Thank you so much !!!
But, where are libnut and librtmp?

Cheers
JIA

> **rubylaser said:**
> If you want to use those packages, you're going to need to compile them, here are some nice directions to get it working for you.
[http://ubuntuforums.org/showpost.php?p=9114176&postcount=967]("http://ubuntuforums.org/showpost.php?p=9114176&postcount=967")

---

### Post by Yellow Pasque on 2010-07-20
You can get librtmp(-dev) and libvpx(-dev) here:
[https://launchpad.net/~lucid-bleed/+archive/lucidbleed-exp/+packages](https://launchpad.net/~lucid-bleed/+archive/lucidbleed-exp/+packages)

You can build libnut like so (use checkinstall if you want to build a .deb):
```
sudo apt-get install subversion
cd /opt
sudo svn co svn://svn.mplayerhq.hu/nut/src/trunk/ nut
cd nut
sudo make
sudo make install
sudo ldconfig
```

---

### Post by Messobage on 2010-07-20
[http://cvs.openpkg.org/fileview?f=openpkg-src/libnut/libnut.spec](http://cvs.openpkg.org/fileview?f=openpkg-src/libnut/libnut.spec)
 
 
> **jiapei100 said:**
> Thank you so much !!!
But, where are libnut and librtmp?
 
Cheers
JIA

---

### Post by jiapei100 on 2010-07-20
Hi, Temüjin:
Thank you so much for your kind help.
It seems the only thing I need to do is add
[https://launchpad.net/~lucid-bleed/+archive/ppa](https://launchpad.net/~lucid-bleed/+archive/ppa) and
[https://launchpad.net/~lucid-bleed/+archive/lucidbleed-exp](https://launchpad.net/~lucid-bleed/+archive/lucidbleed-exp)
to my /etc/apt/sources.list, right?

I found librtmp from [http://rtmpdump.mplayerhq.hu/](http://rtmpdump.mplayerhq.hu/)
But, it doesn't afford a configuration.
What I need to do is 
"make SYS=posix"
and then install it.

However, some of the packages, I really would like to specify the installation folder. I mean, I prefer discriminate
/usr and /usr/local 

If I can do "./configure", I can specify the folder to install by "./configure --prefix=/usr"
but now, I can't do it for rtmpdump.

Can you please give me a hand please?

Cheers
JIA


> **Temüjin said:**
> You can get librtmp(-dev) and libvpx(-dev) here:
[https://launchpad.net/~lucid-bleed/+archive/lucidbleed-exp/+packages](https://launchpad.net/~lucid-bleed/+archive/lucidbleed-exp/+packages)

You can build libnut like so (use checkinstall if you want to build a .deb):
```
sudo apt-get install subversion
cd /opt
sudo svn co svn://svn.mplayerhq.hu/nut/src/trunk/ nut
cd nut
sudo make
sudo make install
sudo ldconfig
```

---

### Post by jiapei100 on 2010-07-20
Yes, as for nut,
it's the same.
Without ./configure, how can I install it into /usr, rather than /usr/local ?

Cheers
JIA

> **Temüjin said:**
> You can get librtmp(-dev) and libvpx(-dev) here:
[https://launchpad.net/~lucid-bleed/+archive/lucidbleed-exp/+packages](https://launchpad.net/~lucid-bleed/+archive/lucidbleed-exp/+packages)

You can build libnut like so (use checkinstall if you want to build a .deb):
```
sudo apt-get install subversion
cd /opt
sudo svn co svn://svn.mplayerhq.hu/nut/src/trunk/ nut
cd nut
sudo make
sudo make install
sudo ldconfig
```

---

### Post by jiapei100 on 2010-07-20
alright, I found the easiest way is to edit
Makefile directly.

Cheers
JIA

---

### Post by highlandsun on 2010-07-20
For rtmpdump and librtmp:

  make install prefix=/usr

The Makefile should never need editing.

---

