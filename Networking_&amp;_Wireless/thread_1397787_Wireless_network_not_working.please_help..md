---
title: "Wireless network not working.please help."
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by Viscous Biscuits on 2010-02-03
I just recently installed Ubuntu 9.10 on a dell laptop.  My wi-fi connection that ive been using on the same computer for years is not working when i log on.  However if i run the burnt image cd and choose the option "Use Ubuntu without making any changes to your computer" i am asked if i want install proprietary drivers.  If i activate one "Broadcom STA" i can connect to the wireless connection in my house.  When im using the version installed on my laptop it doesnt ask me if i want to install the drivers and it doesnt even find them when i go to hardware drivers under system.  So to sum it up I can get connection when i run Ubuntu from the cd but not when i run the Ubuntu on my laptop.   
Any help would be greatly appreciated.

---

### Post by Brad Berger on 2010-02-03
I had a similar problem recently on a laptop with a Dell wireless 1390 802.11g mini-pci card in it. This post helped:   [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)  Following the instructions in the section "Installing Drivers for the BCM43xx Cards" worked for me.

---

### Post by bkratz on 2010-02-03
If you type lspci (LSPCI) in lowercase and see which Broadcom (if any) device (BCMxxxx) is used. You then can look at this thread for help.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by Iowan on 2010-02-03
[Here]("http://ubuntuforums.org/showpost.php?p=8766120&postcount=5") is a post regarding the STA kernel/driver.

The link by **bkratz** looks promising, too.

---

