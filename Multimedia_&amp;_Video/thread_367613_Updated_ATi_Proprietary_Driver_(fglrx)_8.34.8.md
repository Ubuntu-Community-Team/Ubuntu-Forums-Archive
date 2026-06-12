---
title: "Updated: ATi Proprietary Driver (fglrx) 8.34.8"
date: 2007-02-22
forum: Multimedia &amp; Video
---

### Post by dasunst3r on 2007-02-22
I just wanted to let you all know that as of 2/21/2007, the fglrx driver has been updated to 8.34.8.  

For those of you who are having trouble with suspend/resume, you should install this updated driver.  Go get it!  [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

Source: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.34.8.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.34.8.html)

---

### Post by pay on 2007-02-23
It still doesn't support aiglx.... sigh

---

### Post by lucid2 on 2007-02-27
I updated drivers but the problem with resume after suspend still exist. :|

My ATI card is mobility x1600 and laptop benq p52.
i also try with edit 

/etc/default/acpi-support 

but any solution that i foud here doesn't work ;|

---

### Post by nardis_Miles1 on 2007-03-13
I don't know whether any of you have been having difficulty installing the new (8.34.8) driver. You will only know it if you are using the 3d acceleration. That is, X will start, and it will seem that the install went very well. However, the dri will not start. Here are the things I had to do to get things really to work.

1. There is an error in ati-installer.sh that is part of the fglrx-install temporary directory. Specifically, the atiogl_a_dri.so link is broken. My cludge was to issue the command

ati-driver-installer-8.34.8-x86.x86_64.run --extract DIR

so that the contents are extracted into DIR

Then, edit ati-installer.sh and comment the line containing atiogl_a that is appropriate for your architecture.

Simply to build the module fglrx.ko, you issue the command

ati-installer.sh 8.34.8 --build

The module will be placed in the directory in /lib/modules/2.6.x/misc directory. You will have to change the linux-restricted-modules-common file under /etc/default
so that the fglrx module is not loaded.

2. Now, this was the last move. When I first tried to load the module, I was told that /sbin/lrm-video was not found. I had to install 

linux-restricted-modules-comn-2.6.17-11.2

even though I'm running a 2.6.19 kernel. lrm-video is contained in the linux-restricted-modules...
package.

Now everything seems to work very nicely.

I'm sure there is a more elegant solution, involving building deb's with the ati-installer.  However, this did work!

---

