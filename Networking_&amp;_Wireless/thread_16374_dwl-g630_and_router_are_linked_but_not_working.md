---
title: "dwl-g630 and router are linked but not working"
date: 2005-02-21
forum: Networking &amp; Wireless
---

### Post by billd414 on 2005-02-21
I have a dlink dwl-g630 pcmcia card in my dell inspiron 3800 running Ubuntu warty and a dlink wireless router that appear to be communicating in some way (the lights on the card blink the way they are supposed to when connected, if I do ifconfig wlan0 it shows the correct hardware address, inet address assigned by the router, and shows that packets are being transmitted and received with no errors or dropped packets)
     If I do iwconfig wlan0 it shows the proper essid, the right encryption key and access point address but shows a link quality of 0/100 which is definitly no good.
     I used ndiswrapper and the drivers from the disk that came with the card to be able to see the card and iwconfig to get it to this point but Gnome does not see it and I cannot set it up with the network configuration GUI with dhcp or manual setup and if I try sometimes it will lock up the desktop and I have to reboot to start over. I know I am missing something but being new to Linux I don't know what it is, so any help would be greatly appreciated, especially if anyone has seen a situation like this.

     Thanks, Bill

---

