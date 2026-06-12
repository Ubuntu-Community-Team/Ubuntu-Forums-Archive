---
title: "I accidentially removed Network manager+ WLAN adapter does't work"
date: 2011-03-27
forum: Networking &amp; Wireless
---

### Post by 19urs89 on 2011-03-27
Hello,

I tried to fix my wlan adapter troubles, and I made it worse. Following advice on a forum that gave a thread of a person with similar wireless networking problems; I removed NetworkManager.

I have a wlan adapter that does not work properly on ubuntu 10.10. It cannot be turned on/off by pressing Fn + F3. The WLAN LED indicator blinks sometimes, then it's on for a few minutes, then it goes out for a few minutes. While the WLAN LED is blinking or out, the wireless network does not work. While it's on, the wireless network works correctly for a few minutes. After a few minutes, the network connection is broken again. Could it be a driver problem? 

A very strange fact: My wired Ethernet network adapter works perfectly.




Thanks to anyone who wants to help me with my technical problem!!!

My PC: ACER ASPIRE 5742Z
My wireless network adapter: Atheros AR9287


fred

UPDATE: NetworkManager is reinstalled. The WLAN adapter is still malfunctioning.

---

### Post by jujubees on 2011-03-27
not sure if we have the same problem, but heres my situation:

network manager would re-establish my connection every few minutes causing lag while gaming, so i uninstalled it.
i can manually connect to my wireless router using this script:

#!/bin/bash
sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid "dd-wrt"  //network name
sudo iwconfig wlan0 ap 00:23:69:5C:A9:71  //routers wireless mac
sudo ifconfig wlan0 192.168.1.131
sudo route add default gw 192.168.1.1  //gateway
sudo ifconfig wlan0 up
exit 0

note that i don't have any security on my network.

---

### Post by TBABill on 2011-03-27
Possibly something here of assistance?

[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/139022](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/139022)

---

