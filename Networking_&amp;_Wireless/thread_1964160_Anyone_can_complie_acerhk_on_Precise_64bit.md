---
title: "Anyone can complie acerhk on Precise 64bit?"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by leorolla on 2012-04-23
I have tried different versions of the *acerhk* source code, with different solutions that I found googleing, and nothing works here.

Installing *acerhk-source* from repositories halts on the *make* step.

Even in Maverick 32 bit PAE I got the the same result:

```
sudo apt-get install linux-headers-generic
sudo apt-get install acerhk-source
sudo -e /usr/src/linux-headers-`uname -r`/Makefile
# REMOVE LINE WITH PG FLAG
cp /usr/src/acerhk.tar.bz2 /tmp
cd /tmp
tar -xf acerhk.tar.bz2
cd /tmp/modules/acerhk
make
# HALTS
```It used to work perfectly in Lucid.

Any help is welcome :)

Thanks.

---

### Post by praseodym on 2012-04-23
Hi,

you need some special source code from 11.04 and on:

```
sudo apt-get install dkms build-essential
wget https://launchpad.net/~cogito-16/+archive/ppa/+files/acerhk-source_0.5.35-14_all.deb
sudo dpkg -i acer*.deb
sudo dkms add -m acerhk -v 0.5.35 
sudo dkms build -m acerhk -v 0.5.35 
sudo dkms install -m acerhk -v 0.5.35 
```
Adjustment of the Makefile is not necessary. You may want to install the PPA:

[https://launchpad.net/~cogito-16/+archive/ppa/](https://launchpad.net/~cogito-16/+archive/ppa/)

---

### Post by leorolla on 2012-04-23
Thank you very much!
 So it also works on 64bit architeture?

I don't understand why this is not easy to find googling...

Cheers,
Leo

---
Edit: I had posted som error messages before.
Never mind, I realize I'm trying on Ubuntu 10.10 and you said 11.04.
Will try it on 12.04 tomorrow.
---

---

