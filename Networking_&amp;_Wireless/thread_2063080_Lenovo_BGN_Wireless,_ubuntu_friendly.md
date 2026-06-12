---
title: "Lenovo BGN Wireless, ubuntu friendly?"
date: 2012-09-26
forum: Networking &amp; Wireless
---

### Post by fiftyeightz on 2012-09-26
I'm looking at the Lenovo G780 laptop:
[http://shop.lenovo.com/us/laptops/essential/g-series/g780](http://shop.lenovo.com/us/laptops/essential/g-series/g780)

The wireless appears to be "Lenovo BGN Wireless"

from what I know often the laptop distributor (e.g Dell)  doesn't manufacture the wireless device, so I don't know what this wireless is, and if it'll will work with Ubuntu.

Couldn't find any info on it so far.

Anyone have any idea?

---

### Post by OrangeCrate on 2012-09-26
Deleted.

---

### Post by OrangeCrate on 2012-09-26
Deleted.

---

### Post by kurt18947 on 2012-09-26
I think you are correct to be concerned about wireless functioning.  Who knows what "Lenovo BGN" is?  Is it a rebranded Intel/Broadcom/who-knows chip?   If possible, make sure there's not a restocking fee on a return.  Stores in the U.S. used to charge a 10%-15% restocking fee and put a 2 week return limit on notebooks, cameras and some other electronics to discourage "free rentals".  

Your other choice would be, if the onboard wireless is nonfunctional would be to use a known-to-work nano USB wifi adapter such as the Edimax ew7811Un.  They're pretty unobtrusive.

---

### Post by OrangeCrate on 2012-09-26
Deleted.

---

### Post by fiftyeightz on 2012-09-27
Some news:

I called the Lenovo tech support and managed to find out that the wireless device for G780 (labeled as "Lenovo BGN wireless") is either **Atheros** or **Broadcom**.

They also told its 11 b/g/n

They said the exact model of the Broadcom is not known until order.
and the Atheros model is **AR8162**

They said that I can specify I want Atheros upon ordering

From googling I found:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1046435](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1046435) - says it's not compatible

[http://askubuntu.com/questions/157223/12-04-does-not-detect-eth0atheros-ar8162](http://askubuntu.com/questions/157223/12-04-does-not-detect-eth0atheros-ar8162) - this guy managed to fix it 

[http://ubuntuforums.org/showthread.php?t=2050126](http://ubuntuforums.org/showthread.php?t=2050126) - also this guy

Looks like it won't work out of the box, right?
Probably better then Broadcom though, right?

---

### Post by kurt18947 on 2012-09-27
I've not dealt with that Atheros chip so I can't say.   It sometimes takes a while for support for new chipsets to appear for linux.  Personally I'd probably opt for Atheros over Broadcom but I have no experience with the latest chips from either manufacturer.  Looking at this page:

[http://www.linuxfoundation.org/collaborate/workgroups/networking/alx](http://www.linuxfoundation.org/collaborate/workgroups/networking/alx)

it looks like the Atheros 8162 is a fast ethernet e.g. wired ethernet chip.  I wonder if the driver works on wireless as well.  There's always NDISwapper though my experience with NDISwrapper hasn't been sterling.  Another consideration is that NDISwrapper only works with Windows XP drivers and the 'bitness' has to match.  If the linux O.S. is 64 bit NDISwrapper would require Windows XP 64 bit drivers.

---

### Post by fiftyeightz on 2012-09-27
> **kurt18947 said:**
> I've not dealt with that Atheros chip so I can't say.   It sometimes takes a while for support for new chipsets to appear for linux.  Personally I'd probably opt for Atheros over Broadcom but I have no experience with the latest chips from either manufacturer.  Looking at this page:

[http://www.linuxfoundation.org/collaborate/workgroups/networking/alx](http://www.linuxfoundation.org/collaborate/workgroups/networking/alx)

it looks like the Atheros 8162 is a fast ethernet e.g. wired ethernet chip.  I wonder if the driver works on wireless as well.  There's always NDISwapper though my experience with NDISwrapper hasn't been sterling.  Another consideration is that NDISwrapper only works with Windows XP drivers and the 'bitness' has to match.  If the linux O.S. is 64 bit NDISwrapper would require Windows XP 64 bit drivers.

Weird, I assume it's wireless too.
On the product page for G780 there's only one network device, so that eliminates the possibility that the support guy referred to a different device.

---

### Post by kurt18947 on 2012-09-28
> **fiftyeightz said:**
> Weird, I assume it's wireless too.
On the product page for G780 there's only one network device, so that eliminates the possibility that the support guy referred to a different device.

I'm not sure.  Other sources also referred to to the Atheros as an ethernet/wired chip.  I wonder if the Atheros chip is the wired ethernet and you get whatever Broadcom chip is cheapest that day for wireless.  Don't know though.  My understanding is that  Lenovo is one what whitelists WiFi mini-pci cards so you can't just remove the existing card and substitute just any (Linux compatible) mini-pci card, it has to be 'blessed' by Lenovo.

---

### Post by fiftyeightz on 2012-09-28
I'll be calling Lenovo again, very annoying if they gave me the wrong information

---

