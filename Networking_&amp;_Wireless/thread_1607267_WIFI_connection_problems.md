---
title: "WIFI connection problems"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by 351Cleveland on 2010-10-27
Hi guys!
This is my first post to the Ubuntu community, i've just replaced my old WinXP with Ubuntu 9.10. First thing i did after install was trying to get my internet-connection up and running. Since im total noob ive just been going step-by-step from useful threads i've found.
 
I've successfully installed my netgear usb-wifi with ndiswrapper and it finds my wifi-network, but i cant connect to it unless i disable security on the router. I've tried connecting with my hex WEP-key but it doesn't work. I just get prompted to provide network password over and over. I have even changed the password on the router just to be sure im providing the correct one. 
 
Even when connected on disabled security-mode i'm having serious issues, connection seems go up & down and it's very slow when working.
 
I really cant have my wifi unsecured, and the slow connection is nearly unsurfable. Can you guys guide me where to find more information about my problem?
 
i've searched forums but couldn't relate threads to my problem. Would really like to give Ubuntu a chance...
 
// 351Cleveland

---

### Post by utilitytrack on 2010-10-27
Just interesting, what the device do you use exactly? Post here output of **$ lsusb**

---

### Post by 351Cleveland on 2010-10-27
Thanks for your reply. Here's the lsusb ouput:

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1385:5f01 Netgear, Inc WPN111 (no firmware)
Bus 001 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by 351Cleveland on 2010-10-28
Tonight i've been able to connect _once_ with *WEP2 Personal-*key. Connection was very unstable and dropped after ~30s.
 
One question i have about the **$ lsusb** output is the:
 
Bus 001 Device 004: ID 1385:5f01 Netgear, Inc WPN111 **(no firmware)**
 
Whats up with the no firmware? Could this be fixed?
 
 
When i try to reconnect with my WEP2-key the **$ iwconfig** output looks like this:
 
IEEE 802.11g ESSID: "Hummernet"
Mode: Managed Frequency: 2.46GHz Accesspoint: xx:xx:xx:xx
Bit Rate: 54 Mb/s Link Quality: **10/100 **Signal Level: -86 dBm Noise Level: -96 dBm
 
Link quality looks very low. Any suggestions about this and the'**no firmware**'?
 
// 351Cleveland

---

### Post by utilitytrack on 2010-10-28
**351Cleveland**

Look around the forum, here is many people who are able to set up internet with your hardware. For example:

1) [http://ubuntuforums.org/showpost.php?p=7487917&postcount=3]("http://ubuntuforums.org/showpost.php?p=7487917&postcount=3")

2) [http://ubuntuforums.org/showthread.php?t=844856]("http://ubuntuforums.org/showthread.php?t=844856")

Good luck.
[SIZE="1"]
PS
Don't use WEP. Use WPA instead.[/SIZE]

---

