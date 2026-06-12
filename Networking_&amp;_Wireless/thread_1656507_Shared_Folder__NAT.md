---
title: "Shared Folder / NAT"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by johnmay on 2010-12-31
I am using a Guest XP USB wireless connection to connect 10.10 Host to network through Virtualbox.

I would like to share a directory on Host to a separate 10.04 installation. 

I am able to see share in Guest.  I can see the Guest shared docs from the 10.04 machine

The link to the network target from guest to 10.10 Host is not able to be opened.

XP and 10.04 are on 192.168.77.x

The 10.10 machine is on 192.168.0.x

Any ideas?

Background: I was not able to find 64bit drivers to use ndiswrapper for my USB wireless. I have shared the wireless from XP guest to the 10.10 host.

---

### Post by PatchesTheCaveman on 2010-12-31
First let me see if I can get your USB wireless adapter working natively in Linux.  That would be much simpler.

What model USB wireless adapter do you have?

ETA:  I can also troubleshoot your shared folder issue too if you want still want to use XP in VirtualBox for other things.  But having your USB wireless adapter run natively under Linux would be far more efficient.  And the fix for that might break the shared folder setup if we do it now.

---

### Post by johnmay on 2010-12-31
I am using netgear wnda3100 v2 as the wireless USB adapter. It has a broadcom chip set.
 
The 10.10 64 bit  has no native drivers (windows or otherwise) for the chipset. So ndiswrapper only helps on 32bit OS. 

As you can see from this thread" [http://ubuntuforums.org/showthread.php?t=1383708](http://ubuntuforums.org/showthread.php?t=1383708)

There is generally some trouble getting Ubuntu to recognize the wireless.

That is why I am using the shared network connection form the virtualbox XP guest. It is like the drivers were written for it!


Let me know if you would like more information.
Thanks!

---

### Post by PatchesTheCaveman on 2010-12-31
Ubuntu 10.10 Maverick Meerkat (32 and 64 bit) has native support for most Broadcom chipsets via the official Broadcom STA wireless driver.  It can be installed by going to System > Administration > Additional Drivers, selecting the *Broadcom STA wireless driver* and clicking *Install*.

---

### Post by johnmay on 2011-01-01
Well, in the interest of fun, I have actually upgraded the 10.10 to Natty Narwhal.

The upgrade has solved my sound card problem, though I am not able to use my XP guest in VirtualBox.

Also, I am not able to see any drivers in System -> Administration -> Additional Drivers 


Would I have to be connected to the web to find those?

Thanks!

---

### Post by PatchesTheCaveman on 2011-01-01
If you plug into a wired connection, you can run this command to install the STA driver:
```
sudo apt-get install bcmwl-kernel-source
```

Assuming that package is available in the 11.04 alpha.  I have no idea.

You could also give the brand spanking new brcm80211 driver a shot.  This poster explains how and says they work well on natty:  [http://ubuntuforums.org/showpost.php?p=10284103&postcount=54](http://ubuntuforums.org/showpost.php?p=10284103&postcount=54)

---

### Post by johnmay on 2011-01-01
I have a linksys which works OTB on each installation I have tried so far, so I will download the drivers that you suggested. 

Then I will look into the brand new driver you mentioned. 

Thanks for all the info, now I guess I get to decide if I would rather have sound or a direct  internet connection... 

hmm the choice is clear really...

---

