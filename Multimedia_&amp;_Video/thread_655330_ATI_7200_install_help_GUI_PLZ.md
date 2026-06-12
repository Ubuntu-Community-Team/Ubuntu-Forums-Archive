---
title: "ATI 7200 install help GUI PLZ"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by ne_plus_ultra_1 on 2008-01-01
I am using some 2001 nvidia card right now but due to restricted drivers I have elected to install a Radeon 7200 PCI instead.  It works just fine until login screen and then goes black.  

SO, I have nvidia agp and ati pci installed now.  The nvidia locked me into 800x600 down from 1280x960 after I tried using restricted drivers.  That was most inconvenient.  NOW, after REMOVING restricted drivers, I either boot into my proper resolution or into 800x600, there's no telling which is going to happen.

I would like to get the ATI card working but I don't know enough about it to install basic drivers or anything.  Can anyone help with a GUI install of this PLZ?

Best,
-ultra

---

### Post by kshane on 2008-01-01
> **ne_plus_ultra_1 said:**
> 
I would like to get the ATI card working but I don't know enough about it to install basic drivers or anything.  Can anyone help with a GUI install of this PLZ?

Best,
-ultra

You should download the most recent driver (the ATI 7-12).  Once you have it on your system, CD to the directory where it is and ...

```

sudo .sh ./ati_driver_name

```

It will give you a GUI to install the proprietary driver.  The recent driver should work well for your card...

Kevin

---

### Post by ne_plus_ultra_1 on 2008-01-01
Sounds worth a try.

They claim that the most recent driver is only for as old as the 8500 though.

Any thoughts on that?

---

