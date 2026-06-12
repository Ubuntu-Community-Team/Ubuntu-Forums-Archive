---
title: "Wireless Randomly Dropping / Random Slowdowns"
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by telepathetic on 2010-12-08
Please please help!  I've spent many hours on the forums and am totally confused about what to do/try.  I've tried a few things but nothing seems to work.

I just did a fresh install of 64bit 10.10 Maverick Meerkat on my Dell Precision m2400 and fully updated it.
According to Windows (got a dual boot setup) I have a Dell Wireless 1510 Wireless-N WLAN Mini-Card.
I used Administration->Additional Drivers to install the STA Broadcom Driver.

And now my wireless is totally frustrating, mostly useless.  It will only connect sometimes, and when it does it generally drops it's connection within 10 minutes or so.  I can't seem to correlate to anything in particular.  Even when it is "connected" it occasionally seems to have normal download speeds, but most often it is excruciatingly slow, or it will just outright fail to do anything altogether for a long time.

On my Windows side, everything is working fine, so it's definitely not a hardware issue-- must be a driver issue.  

Here are some of the driver details from the Windows side in case it helps:
Dell Wireless 1510 Wireless-N WLAN Mini-Card
Provider: Broadcom Corporation
File Version 5.30.21.0
Driver Date: 10/1/2008

Super Details:
Service: BCM43XX
Location information: PCI bus 12, device 0, function 0
Physical Device Object name: \Device\NTPNP_PCI0021
Inf section: BCM43XNMBO_NT61
Inf section extension: .NTAMD64


What should I do?  I'm happy to run any commands and provide any info that would help.  Thank you in advance for any help!

(It's taken me an hour just to get this post up, cuz I keep getting dropped, or submitting my post keeps timing out)

---

### Post by telepathetic on 2010-12-09
Solution:

Go to this link:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Download for your cpu and follow the README instructions.  The README instructions tell you how to build the driver yourself.  At the bottom they also tell you that you can choose the easier solution of letting ubuntu install everything.  This latter solution is exactly the solution that does NOT work, so don't do it.  Follow the instructions for building the driver yourself, and that totally fixed my issues.  I'm downloading/uploading again at blinding speeds and no dropouts.  I'm very very happy now.

Hopefully this helps someone else.

Why didn't the official supported method work? (Turning on STA in the Hardware Drivers)
The ubuntu drivers must be behind?  That's my only guess (even though the documentation claims that they are kept up to date, they are apparently not).  Or it's just fetching the wrong drivers altogether.

---

