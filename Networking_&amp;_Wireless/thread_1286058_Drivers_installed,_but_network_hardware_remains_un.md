---
title: "Drivers installed, but network hardware remains unclaimed"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by klouchis on 2009-10-08
Here is what I've done on my machine so far
1) installed ubuntu 9.04
2) set up wireless drivers using ndiswrapper (im sure it's the correct driver)
3) blacklisted other native drivers

Here is the segment from lshw for my wireless chip

> lshw
*-network UNCLAIMED     
       description: Network controller
       product: WiMAX/WiFi Link 5050 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0It shows that the card is unclaimed, there is no logical name given for the interface, and the configuration seems very lacking.


ndiswrapper is running as well


> lsmod|grep ndis
ndiswrapper           193436  0 The device is being detected

> lspci -nn | grep Network
04:00.0 Network controller [0280]: Intel Corporation WiMAX/WiFi Link 5050 Series [8086:423d]and the drivers set up by ndiswrapper seem to be good,

> 
ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netw5x32 : driver installed
    device (8086:423D) presentThe only thing I see that's out of place is the warning about the config file, I'm going to try changing ndiswrapper to ndiswrapper.conf and same for blacklist to see if that clears up my problem, but something tells me it wont help me out.  If anyone has any ideas please let me know I would appreciate any help.

EDIT: I changed the ndiswrapper config files to .conf with no change.


Kevin

---

### Post by RainKing44 on 2009-10-25
Have you had any luck? I'm having the exact same problem with a Wireless WiFi Link 5100.

---

### Post by armersuender on 2009-10-26
same problem here, I just got an Asus U50a, and the wifi set up is not happiness.
has anyone found a way yet?

: )

---

### Post by Iowan on 2009-10-26
A couple of links that may/not be helpful:
[http://ubuntuforums.org/showthread.php?t=1289484]("http://ubuntuforums.org/showthread.php?t=1289484")
[http://ubuntuforums.org/showpost.php?p=8118454&postcount=10]("http://ubuntuforums.org/showpost.php?p=8118454&postcount=10")

---

