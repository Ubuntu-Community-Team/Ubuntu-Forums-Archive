---
title: "cr-48 Gobi2000 working(so far)"
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by knightzac18 on 2011-02-14
Getting the cr-48's Gobi2000 verizon CDMA working on Ubuntu 10.10.

So I kept hammering my head why the whole process of getting the verizon wireless gobi2000 to work if it's based on a linux kernel and we are using the chrome kernel to boot...

So I went into the cr-48 dev mode and looked at what chrome-os was doing to use the gobi, found this QCNET driver that ubuntu didn't have...so I looked in the kernel and it was there...but ubuntu wouldn't use it!...so I come to find out it's in the 2.6..../chromeos/drivers not 2.6..../drivers well ubuntu could care less about the chromeos folder, so I copied the gobi folder into the 2.6/drivers directory...rebooted and walla gobi came up in the network manager and everything...I don't know how good it works as I have horrible verizon reception...I do know that wvdial can see it and recognize it...but since I have bad reception it did not wanna connect to easily...

If I manage to get it working any better I will post a more in depth tutorial on what I did!

**Update:** Also, make sure you have activated your verizon account BEFORE you try to use the mobile broadband on ubuntu. If you haven't go back to chrome and activate it first.

---

### Post by Dygear on 2011-02-28
I hate to be a noob, but I will anyway. Where and how did you get access to **/chromeos/drivers** under Ubuntu? Because I'm not seeing this directory in my filesystem. Did you have to mount a file system in order to get to this directory?

(Just so we are clear, my install is also uses the ChromeOS Kernal, it's a dual boot between the CrOS and Ubuntu.)

---

### Post by knightzac18 on 2011-03-01
It copies over with the kernel when you make your ubuntu install, so you don't have to mount anything just go to your kernel folder in ubuntu and everything that chrome has kernel wise should be in there..


Also as of yet I still have yet to actually get it to connect, so far it dials but just dies before it can connect..It does show loading the driver from chrome though.

Once i get some more time I'm going to copy some more stuff off the chrome OS, like the modem status scripts and such to see if I can figure out why ubuntu isn't connecting properly.

---

### Post by Dygear on 2011-03-02
If you do get it working I would love to hear about it, thank you for the attempt!

---

### Post by defconoii on 2011-04-17
Here is how to get 3G working on the Google CR-48 Netbook:
[http://cr48.wikispaces.com/Use+3G+Wireless+in+Ubuntu](http://cr48.wikispaces.com/Use+3G+Wireless+in+Ubuntu)

---

