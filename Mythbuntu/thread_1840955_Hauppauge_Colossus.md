---
title: "Hauppauge Colossus"
date: 2011-09-08
forum: Mythbuntu
---

### Post by stefanst on 2011-09-08
I've been running mythbuntu for more than two years now and my current setup contains an Hauppauge HD PVR on a dedicated backend as well as two frontends. I'm recording from a STB off of Verizon FIOS in HD, hence the need for the HD PVR.

Now I'd like to record from two STBs and I've found this beauty on Newegg:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815116065](http://www.newegg.com/Product/Product.aspx?Item=N82E16815116065)

It looks to me like it's pretty much a PCIe version of the HD-PVR. However, I was unable to find any link to this having been implemented on LinuxTV yet.

Any pointers on if it will work for me?

ST

---

### Post by klc5555 on 2011-09-08
No Linux drivers have been developed yet for the Colossus.

---

### Post by nickrout on 2011-09-08
> **klc5555 said:**
> No Linux drivers have been developed yet for the Colossus.And as I understand it, never will be. The chipset manufacturer is not interested in supporting free|open software.

---

### Post by carra on 2012-01-24
Maybe [this card]("http://www.ieiworld.com/product_groups/industrial/content.aspx?gid=09049535992720993533&cid=09049577938864496628&id=0B144541960448111382") would do the trick? :D
.

---

### Post by nickrout on 2012-01-24
> **carra said:**
> Maybe [this card]("http://www.ieiworld.com/product_groups/industrial/content.aspx?gid=09049535992720993533&cid=09049577938864496628&id=0B144541960448111382") would do the trick? :D
.

How? At first glance I do not see any linux drivers.

---

### Post by thatguruguy on 2012-01-24
> **carra said:**
> Maybe [this card]("http://www.ieiworld.com/product_groups/industrial/content.aspx?gid=09049535992720993533&cid=09049577938864496628&id=0B144541960448111382") would do the trick? :grin:
.

> **nickrout said:**
> How? At first glance I do not see any linux drivers.

The web site linked by carra states that the card supports Linux Kernel 2.6.27. I don't know if this means that the drivers are now part of the Linux kernel or not, although that is apparently what they are claiming.

Nick, do you have any specific information suggesting that this card is not supported?

---

### Post by iamlindoro on 2012-01-24
The driver they provide is a custom one-off closed source thing that does not support standard linux capture APIs.  It therefore cannot be used with MythTV.  Someone could theoretically try to write a reverse-engineered open source driver for it or write a brand new recorder for MythTV for this one device, but until one of those happens, the card is of no use in MythTV.

---

### Post by nickrout on 2012-01-24
> **iamlindoro said:**
> The driver they provide is a custom one-off closed source thing that does not support standard linux capture APIs.  It therefore cannot be used with MythTV.  Someone could theoretically try to write a reverse-engineered open source driver for it or write a brand new recorder for MythTV for this one device, but until one of those happens, the card is of no use in MythTV.

What he said!

---

### Post by nightwar on 2012-02-01
You will run into HDCP issues capturing from an STB.  

Id love to have a component card that work in linux(like the hd-pvr)  except pci,etc instead of USB

---

### Post by nickrout on 2012-02-01
> **nightwar said:**
> You will run into HDCP issues capturing from an STB.  

Id love to have a component card that work in linux(like the hd-pvr)  except pci,etc instead of USB

Whats wrong with USB? (apart from another box and wall wart?)

---

