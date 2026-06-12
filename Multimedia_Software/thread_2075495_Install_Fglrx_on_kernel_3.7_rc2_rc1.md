---
title: "Install Fglrx on kernel 3.7 rc2 rc1"
date: 2012-10-24
forum: Multimedia Software
---

### Post by somesayinice on 2012-10-24
I'm probably less than a noob so please bear with me.

I had been planning to write a long post about how I got this to work but kernel panic twice. 3.7 rc2 I guess not stable on my system even after normal boot.  System boots without a hitch though with fglrx.  I suspect the below works for rc1 too.  Long and short is to patch firegl_public.c with [http://catalyst.apocalypsus.net/files/arch-fglrx-3.7.patch](http://catalyst.apocalypsus.net/files/arch-fglrx-3.7.patch)
But here's the abridged version:

Download this (pre-packaged deb I made):
[https://docs.google.com/open?id=0B3zsQZuzqkhzR05IbzBINGdWRXM](https://docs.google.com/open?id=0B3zsQZuzqkhzR05IbzBINGdWRXM)

version.h is not in the normal place so
**$ *ln -s /usr/src/linux-headers-3.7.0-030700rc2-generic/include/generated/uapi/linux/version.h /usr/src/linux-headers-3.7.0-030700rc2-generic/include/linux/version.h***
- The above and this [http://rglinuxtech.com/2012/10/15/3-7-rc1-problems/](http://rglinuxtech.com/2012/10/15/3-7-rc1-problems/) will also help for installing on NVIDIA cards.

Install kernel 3.7 rc2 from: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc2-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc2-raring/)
**- Make sure to install the headers_all deb**
Download debs and $sudo dpkg -i *rc2*.deb

Afterwards:
$sudo dpkg -i fglrx_9.0_3.7.0_rc2.deb

You're good to go with reboot.

Will edit OP later.

---

### Post by bosyber on 2013-01-14
thanks, that was useful in getting fglrx (or other external modules I suppose?) to work on 3.7.1 from kernel-ppa.

---

