---
title: "wireless authentification problem"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by Karychy on 2009-02-21
Hey, I have what I hope is an easy-to-solve problem with my wireless on ubuntu 8.10.
Ubuntu detects the network, and when I go the the System -> Preferences -> Network configuration, my wireless connection is indeed listed under the Wireless tab. From here on however, I have no idea how to activate it. I tried selecting it from the internet connections icon, was asked for the password, but when I provided it no connection was established. I am sure I am using the right password. There is another number I was given from my Internet provider and this one I don't know where to input. What are the BSSID and MAC address? Am I supposed to provide them, or will they be detected automatically?

Thank you!

---

### Post by superprash2003 on 2009-02-21
go to your terminal and post output of the following commands
1)iwconfig
2)ifconfig

---

### Post by Karychy on 2009-02-21
Ok, thanks! 
So I got lots of things displayed, but 'mac' and 'bssid' arent mentioned anywhere on those two lists. What do I have to look for there exactly?

---

### Post by superprash2003 on 2009-02-22
to view ESSID and MAC address of a wifi router in your area just type **sudo iwlist scanning**

---

### Post by Karychy on 2009-02-27
Ok, I have the MAC address now. Still no luck with he BSSID. The sudo iwlist scanning only displayed the ESSID :(
Am I doing something wrong here? It cant possibly be that hard to make the wireless work :( 

Please help!

---

### Post by Karychy on 2009-03-01
Nevermind, problem solved. Turned out I didn't need the BSSID to make it work. Yet the mystery remains (for me at least) why I was asked for it in the network configuration wizard. 
Anyone feel like pointing me to a 'networking under linux for dummies' kind of tutorial? 

~Kary

---

