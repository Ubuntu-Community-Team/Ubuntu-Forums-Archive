---
title: "Second ATI Graphics Card Not Working"
date: 2008-08-07
forum: Multimedia Software
---

### Post by sshapiro63 on 2008-08-07
Hello All,

I am running Hardy 64-bit (8.04.1) with two ATI cards installed; a 4850 HD as my primary card and a 2400 Pro as a secondary card.

I have installed the latest ATI proprietary driver and it works fine with the 4850. I am running two monitors using the 4850 with no problems. However, I would like to run a third monitor using the 2400 Pro. This card does not show up using the Catalyst Control Center application under Linux, although I can get all the cards working if I boot into Vista or XP.

Is there something I can do to get the 2400 Pro working along with the 4850 HD?

Thanks,

Steve

---

### Post by scheutz2002 on 2008-08-11
Where did you get the driver that worked?  I have tried several
drivers and sources, including xorg-driver-fglrx.  All of them
fail to recognize the 4850 for me.  ATI's site shows no driver
for it either.

---

### Post by markbuntu on 2008-08-12
The linux driver at the ati site does have 4850 support. It was released the same day as the card.

The 8.7 driver from ati has some dual card support. Type

aticonfig --help

in a terminal to see the options.

---

### Post by scheutz2002 on 2008-08-12
_The_ linux driver?  I must not have found the right site.  The
only ati site I have found that offers drivers offers 23 different
drivers for radeon models for linux x86 and the same 23 for linux x86_64.  
None of them have names that resemble 4850.  Is it one
of the 23?  Is there a different site I should be looking at?

---

### Post by scheutz2002 on 2008-08-12
P.S.  Forgot to say, the site I found for ati drivers is
ati.amd.com/support/drivers.html

---

### Post by markbuntu on 2008-08-13
Did you look at the relase notes?

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_87_linux.htm](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_87_linux.htm)

The 4800 series is at the top of one of the lists. Anyway, if you want to install the driver, use this guide, Method 2:


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by scheutz2002 on 2008-08-14
I found those notes _after_ I found the driver itself, at that site.
Don't remember how I got there, it was convoluted, but not through
anything from amd or ati.

---

