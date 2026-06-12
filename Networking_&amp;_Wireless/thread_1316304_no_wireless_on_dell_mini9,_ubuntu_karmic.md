---
title: "no wireless on dell mini9, ubuntu karmic"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by mnoyes on 2009-11-05
It's been days of trying to work through forum posts trying various approaches, but I still can't get wireless to work since upgrading to 9.1.

I upgraded from 9.04, but had various problems, so I did a clean install of 9.1 from a usb stick.

I have only the broadcom STA wireless driver installed. (No b43 or ssb) In hardware drivers I get the "driver is activated but not in use" message. Have tried removing, rebooting, installing, rebooting, etc. to no avail. Have removed the bcmwl package in synaptic and installed again. No luck.

Seem to be some conflict with lib82011 -- but I can't remember where I saw that message...

Network controller is BCM4312 802.11b/g (rev 02)
Ethernet controller is RTL8101E/RTL8102E PDI Express Fast... (rev 02)

lshw -C network, first line, shows
*-network UNCLAIMED

Help?

BTW, all is well on my Dell 1330 running karmic (Pro/wireless (Golan) network connection).

---

### Post by mnoyes on 2009-11-06
And no reply in the forum... It seems the resources are maxed out with the various issues related to 9.1...

---

### Post by ryanmcgavock on 2009-11-08
+1... Just installed UNR 9.1 on an HP Mini and I am having the same problem, unable to detect or create wireless connections. Worked just fine on Ubuntu 9.04.

---

### Post by ASJboarder on 2009-11-09
This worked for me on my Mini 9:
```

[COLOR=blue]sudo apt-get update
[/COLOR]
sudo apt-get --reinstall install bcmwl-kernel-source
```

Found it here:
[http://www.ubuntumini.com/2009/10/ubuntu-910-karmic-koala-beta-is.html](http://www.ubuntumini.com/2009/10/ubuntu-910-karmic-koala-beta-is.html)

---

### Post by xoftware on 2009-11-12
I have had the same problem with 9.10 on UNR, moblin remix, and the desktop version. I have a dell mini 9 and a mini 10 and both had problems with the STA driver (among other things) when installing 9.10, though I haven't tried the command line quoted above (I did try the command line using the option install instead of reinstall with apt-get to no avail). I had done an upgrade from 9.04 to 9.10 with UNR on my mini 9 and the driver worked fine, but I decided to do a clean install and now have that problem. Does anyone know if Canonical is aware of this bug? Well, I am going back to 9.04 until this bug gets straightened out.

---

### Post by cyclopse on 2009-11-12
Exactly the same problem with Dell mini 9. Solution in this thread didn't work for me either. Ubuntu please post a fix for us.

---

### Post by adamruss on 2009-11-12
same for all macbook pro 5,5 - this is shamefull! first creative x-fi now bcmwl - whats up with 9.10?!

---

### Post by johnnybirdman on 2010-01-31
> **ASJboarder said:**
> This worked for me on my Mini 9:
```

[COLOR=blue]sudo apt-get update
[/COLOR]
sudo apt-get --reinstall install bcmwl-kernel-source
```

Found it here:
[http://www.ubuntumini.com/2009/10/ubuntu-910-karmic-koala-beta-is.html](http://www.ubuntumini.com/2009/10/ubuntu-910-karmic-koala-beta-is.html)

Thanks, worked for me on my mini9.
J.

---

