---
title: "Edimax nLITE EW-7711USn"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by hhall on 2009-11-13
Hi.

I know it has cropped up in discussions here and there, but I am not terribly computer-literate, so here's my question:

Has anyone managed to install the wireless "high gain" adapter Edimax nLITE EW-7711USn on Ubuntu 9.10, and if so, how is it done? I gather it runs on something called Ralink Rt 2870, but that doesn't really help me. Can anyone?

I have tried the approach suggested [here]("http://ubuntuforums.org/showthread.php?t=960642"), using the software that can be downloaded from the manufacturer, but it won't work (to be precise, I get error messages at points 12 and 13 in that tutorial). 

Thanks in advance.

---

### Post by lindsay7 on 2009-11-13
That model is for "n" speed routers. I have not use it as I have a "g" router and us that Edimax model on Ubuntu with great success.  If you do not have a "g" speed router you would be better of using the adaptor that I use.

---

### Post by hhall on 2009-11-13
Well, I bought the device because I am allowed to use several neighbours' wireless networks. To be honest, I don't know what routers they use. But in any case, without installing the unit at all, it'll be hard to find out...

---

### Post by hhall on 2009-11-16
Anyone?

---

### Post by hhall on 2009-11-30
Um, does no-one else have this problem? Bump, bump...

---

### Post by pafuin on 2009-12-21
_[COLOR=#0066cc][http://www.filefactory.com/file/af31fg2/n/rt2870-2.6.28-apocolipse.tar.gz](http://www.filefactory.com/file/af31fg2/n/rt2870-2.6.28-apocolipse.tar.gz)[/COLOR]_[]("http://www.filefactory.com/file/af31fg2/n/rt2870-2_6_28-apocolipse_tar_gz")
 
> **hhall said:**
> Um, does no-one else have this problem? Bump, bump...

---

### Post by postadelmaga on 2010-07-22
hello,

in my case (ubu 10.04) is enough to blacklist the module rt2800usb  being loaded instead of rt2870sta ...

Solution: 

[B]add this line at the bottom of /etc/modprobe.d/blacklist.conf

blacklists rt2800usb[/B]

---

### Post by arepisky on 2012-01-09
In case any more users consider buying this Wireless adapter: **it works like a charm**. I have Kubuntu 11.04 64-bit and this adapter worked immediately after plugging in with absolutely no software installation. The reception is also a lot better than that of my integrated adapter.

---

