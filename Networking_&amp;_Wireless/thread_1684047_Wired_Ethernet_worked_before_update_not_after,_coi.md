---
title: "Wired Ethernet worked before update not after, coincidence ???"
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by PeteUK on 2011-02-08
Ok so I’m pretty new to the Ubuntu/Linux lark but so far I have found it such a positive experience I have encouraged family/friends to make the leap to open source. Last week I removed a version of windows vista from a friend’s machine using an Ubuntu boot disk. Formatted the drive so It became a solely Ubuntu drive. Altered a few trivial things to do with the GUI and handed it back to my friend. After a week of flawless (and greatly improved) performance my friend decided to search for and install updates available using the update manager. Sadly however after a reboot they discovered, internet and any wired network access stopped. 



  Now as far as I can tell it is not a hardware problem as all physical connections are unchanged and proved with a laptop to be functional. Secondly the network card displays a green light when connected so I do not believe it to be at fault. 



  From the point of view of Ubuntu the card or specifically eth0 is shown not to exist. It is not visible in the network manager and when I ran “sudo dhclient eth0” It returned that the device is not found. 



  I’m puzzled as how to proceed weather there is a simple solution or many others suffering similar problems.  I welcome any suggestions I have considered trying a new network card but I don’t know if that’s a bit drastic... 



  Thanks In advance :confused:

---

### Post by PeteUK on 2011-02-11
Solved my self. Odl card U/S for some reason. Used this card:
[http://www.maplin.co.uk/pci-10-100-network-interface-card-32002](http://www.maplin.co.uk/pci-10-100-network-interface-card-32002)
 
[COLOR=black][FONT=Verdana]Swapped with old one, no problems no install worked strait out of the box. Intranet access restored.[/FONT][/COLOR]
 8-)

---

