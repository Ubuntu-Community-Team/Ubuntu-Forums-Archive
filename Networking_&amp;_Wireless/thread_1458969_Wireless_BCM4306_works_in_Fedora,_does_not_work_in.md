---
title: "Wireless BCM4306 works in Fedora, does not work in Ubuntu"
date: 2010-04-20
forum: Networking &amp; Wireless
---

### Post by I[E on 2010-04-20
I'm one of the lucky few to have an older Dell laptop (8500) with the 1350 b/g wireless based on broadcom's BCM4306 rev. 3. The PCI ID is 14e4:4320 and according to [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43) it should be supported by the b43 driver, but it doesn't see to work in Ubuntu 9.10. 
I've tried every walk through, tried ndiswrapper (which did work before 8.04) and nothing.
Wireless either shows as device not ready or not connected and shows no networks in the scan.

Wireless does work in Fedora though, right out of the box, full speed with no issues.
Is there a way to use whatever drivers Fedora uses in Ubuntu? So :confused:

Thanks in advance.

---

### Post by I[E on 2010-04-29
No one has any ideas?

---

### Post by klemes on 2010-04-29
These series of chips require the use of special firmware packages to work properly under Linux which fall in the restricted drivers category hence they are not included in the CD but it is left to the end user to download them.Look in the Hardware Drivers if anything is listed there regarding your wireless driver,and if it is simply activate it .If not go ahead and install the package 'b43-fwcutter'.That will take care of things including downloading the corresponding firmware for you.

---

### Post by I[E on 2010-04-29
> **klemes said:**
> These series of chips require the use of special firmware packages to work properly under Linux which fall in the restricted drivers category hence they are not included in the CD but it is left to the end user to download them.Look in the Hardware Drivers if anything is listed there regarding your wireless driver,and if it is simply activate it .If not go ahead and install the package 'b43-fwcutter'.That will take care of things including downloading the corresponding firmware for you.

I've tried both the B43 driver listed in Hardware Drivers and b43-fwcutter (separately) to no avail. With both it seems to recognize the device, but does not see any wireless networks (shows disconnected).
In Fedora it works perfectly on 1st boot after installing. I was just hoping someone had a way to use whatever firmware or drivers from Fedora in Ubuntu.

---

### Post by klemes on 2010-04-29
Just found this: [http://wireless.kernel.org/en/users/Drivers/b43#bcm43xx.2C_b43legacy.2C_b43.2C_softmac.2C..._the_full_story](http://wireless.kernel.org/en/users/Drivers/b43#bcm43xx.2C_b43legacy.2C_b43.2C_softmac.2C..._the_full_story)

And most notably:

Note: If your card is a BCM4306 Rev 2, or only has 802.11b capability, it uses **b43legacy**. All other models use b43.

Could there be the problem?

---

### Post by mcoleman44 on 2010-04-29
Did you try STA listed under sytem>admin>hardware drivers?

---

### Post by I[E on 2010-04-29
> **klemes said:**
> Just found this: [http://wireless.kernel.org/en/users/Drivers/b43#bcm43xx.2C_b43legacy.2C_b43.2C_softmac.2C..._the_full_story](http://wireless.kernel.org/en/users/Drivers/b43#bcm43xx.2C_b43legacy.2C_b43.2C_softmac.2C..._the_full_story)

And most notably:

Note: If your card is a BCM4306 Rev 2, or only has 802.11b capability, it uses **b43legacy**. All other models use b43.

Could there be the problem?

Unfortunately not the PCI-ID is 14e4:4320 and listed as a BCM4306/3. I  gave the b43legacy drivers a shot anyway to no avail.

> **mcoleman44 said:**
> Did you try STA listed under  sytem>admin>hardware drivers?

The only listing under Hardware Drivers is B43

---

### Post by mcoleman44 on 2010-04-29
You could try this:
1 Open Synaptic Pacakage Manager
2 Ensure the LiveCd is in CD drive
3 Settings > Repositories > Ubuntu Software
4 Check the "installable from cd" Box and close
5 Refresh
6 Search for "bcmwl-kernel-source"
7 Mark for installation
8 Install it
9 Reboot computer

---

### Post by klemes on 2010-04-29
Did you try to see what the output of sudo ifconfig & sudo iwconfig is?
Is there a wlan0 interface there somewhere?

---

### Post by I[E on 2010-04-29
> **mcoleman44 said:**
> You could try this:
1 Open Synaptic Pacakage Manager
2 Ensure the LiveCd is in CD drive
3 Settings > Repositories > Ubuntu Software
4 Check the "installable from cd" Box and close
5 Refresh
6 Search for "bcmwl-kernel-source"
7 Mark for installation
8 Install it
9 Reboot computer

The STA driver is for the BCM4311, 4312, 4321, and 4322 devices and just gives me 'device not ready' when I try it.

> **klemes said:**
> Did you try to see what the output of sudo  ifconfig & sudo iwconfig is?
Is there a wlan0 interface there somewhere?

If I use the B43 driver it does show a wlan0 interface, but if I try and scan for networks it returns 0 results.

---

