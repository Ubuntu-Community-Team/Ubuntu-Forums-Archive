---
title: "Wireless configuration on new install"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by schoolys on 2010-01-20
Sorry to all ahead of time, I am a complete beginner on Ubuntu and for todays issue I cant seem to get the wireless to work.   Below is the system info and results.  Any tips on this would be helpful!

**1 ) Machine Brand and Model (PC/Laptop)**:
 	Code:
 	Dell Studio 15 
**2 ) Wireless Brand, Model and Wireless Chipset:**
 	Code:
 	$ lspci
$ lsusb

Broadcom Corporation BCM4312 802.11b/g (rev1)

([COLOR=Red]hint[/COLOR]) use **grep** to get only information about the Wireless
 	Code:
 	$ lspci -nn | grep 'Wireless Brand' 
**3 ) check interface:**
 	Code:
 	$ ifconfig  <----- does not show the adapter
$ iwconfig  <----- shows no wireless extensions 
([COLOR=Red]hint[/COLOR]) if the Wireless interface name is wlan0 you can also use
 	Code:
 	$ iwconfig wlan0 
**4 ) Check for modules:**
 	Code:
 	$ lsmod
I see:   cfg80211     109144   2    b43,mac80211

([COLOR=Red]hint[/COLOR]) search for the Wireless module
 	Code:
 	$ lsmod | grep "wlan_module_name" 
**5 ) Kernel boot messages**
 	Code:
 	$ dmesg
[13.330243] b43-phy0 ERROR: Found Unsupported PHY (analog 6 Type5 Rev1

[1313.330288] B43: probe of ssb0:0 failed eith error -95


([COLOR=Red]hint[/COLOR]) the same as in (4)

**6 ) Network configuration**
 	Code:
 	$ sudo lshw -C network  Interface is shown 
**7 ) Scan for networks:**
 	Code:
 	$ iwlist scan
Wireless interface is not listed here

([COLOR=Red]hint[/COLOR]) the same as in (3)
 	Code:
 	$ iwlist scan wlan0 
**8 ) Ubuntu Version: **
 	Code:
 	$ lsb_release -d   9.10 
**9 ) Kernel/architecture (including 32 vs. 64 bit): **
 	Code:
 	$ uname -mr
2.6.31-14 generic x86_64

**10 ) Restarting the network:**
 	Code:
 	$ sudo /etc/init.d/networking restart
Same

---

### Post by bkratz on 2010-01-20
Here is some useful info

[http://ubuntuforums.org/showthread.php?t=1369260](http://ubuntuforums.org/showthread.php?t=1369260)

main information:
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by schoolys on 2010-01-20
I was able to get the wireless to work following the instructions in an earlier post. The only problem I have now is that I cant get the other part of the config to work for when rebooting. Its a nusance to have to redo the commands to make it work every time but a small price to pay.

---

