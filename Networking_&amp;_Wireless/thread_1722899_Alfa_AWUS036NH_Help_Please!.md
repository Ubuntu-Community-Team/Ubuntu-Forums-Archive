---
title: "Alfa AWUS036NH Help Please!"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by proehc16 on 2011-04-06
I will apologize right now if this is in the wrong section, but I have a question about the Alfa AWUS036NH. I have it installed on ubuntu, 10.04 (Lucid Lynx) and I would like to be able to change the mac address on this device. I use macchanger so the command I type is 
sudo ifconfig wlan0 down
sudo macchanger -r wlan0
sudo ifconfig wlan0 up ( this is where I get problems) It spoofs the mac all the way up to when i bring it back up. I have gotten this device working by just doing 
sudo gedit /etc/modprobe.d/blacklist.conf and blacklist rt2800usb... 
I have also blacklisted the rt2870sta and i was able to spoof the mac but i was unable to select the device from the network manager. I am new to linux so if anyone could help me it would be greatly appreciated!

Thank you!

---

### Post by cosiaca on 2011-05-16
I have the same problem, applying macchanger but it works fine on my internal wifi, with alfa awus036nh macchanger nothing changes.

---

