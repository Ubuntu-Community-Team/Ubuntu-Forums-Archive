---
title: "driver loads but wap not assosciated"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by newguy1 on 2009-12-30
Hi I am a newbie trying to setup wifi using 9.10 on a compaq nx9010 . The driver is activated for the broadcom 4320 rev 2 chipset. the wifi light is on.I am using connecting to the router by an ethernet cable. if I run iwconfig I get:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"simonie"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 8A:4C:E7:91:5A:1E   
          Bit Rate=54 Mb/s   Tx-Power:13 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I am using a lynksys Wireless-N Broadband Router WRT160Nv2

I would appreciate any help. thank you

---

### Post by shredder12 on 2009-12-30
What problem do you face while trying to make a wireless connection?

---

### Post by newguy1 on 2009-12-31
Sometimes, my wireless connection repeatedly attempts to connect to the internet. a box pops up saying asking for the wep password, which I provide, but it can't connect> Other times a connection will be established but I can't browse the WWW.

thanks for looking at this

---

### Post by newguy1 on 2010-01-05
Hi I am a newbie trying to setup wifi using 9.10 on a compaq nx9010 . The driver is activated for the broadcom 4320 rev 2 chipset. the wifi light is on.I can connect to my neighbors's unsecured network, but not min.e which is using personal WPA2 security.

I am using a lynksys Wireless-N Broadband Router WRT160Nv2

I would appreciate any help. thank you

---

### Post by shredder12 on 2010-01-05
I am not sure why you are having this problem.. I searched a bit and found out this bug report in network manager..
Even though it wasn't confirmed but in there was a suggestion to try and use wicd instead of network-manager coz it handles wpa and wpa2 connections better than NM..
you can install it using this command
```
sudo apt-get install wicd
```

---

### Post by newguy1 on 2010-01-05
Thanks for the advice. unfortunately its still not working. I have installed WICD and removed the gnome network manager

WICD  tries to validate authentication which fails. then it tries to obtain an ip address which fails. finally it says: CONNECTION FAILED: UNABLE TO GET IP ADDRESS". meanwhile it is showing the wireless network at 100% signal. 

Any thoughts?


[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by shredder12 on 2010-01-05
have you tried using wep encryption?  and are you able to connect to some other network which uses wpa security?

---

### Post by newguy1 on 2010-01-05
There are other computers on the network which run MS vista and xp pro. I assume to change to wep , I would have to change the modem settings and then the other computers settings. is that correct?

---

### Post by shredder12 on 2010-01-05
If others are able to connect using windows then it doesn't seem to be a router related issue..
Even thogh trying wep will at least ensure that there is some problem while making a connection on wpa secure network.

---

### Post by newguy1 on 2010-01-07
last nite tried changing wifi channel, changing to WEP, installed and tried WPASUPPLICANT and WPA_GUI. Unfortunately , nothing worked. The wifi controller was able to assosciate with the network but could not authenticate. I'm wondering if the passphrase that I type in  on the computer is somehow being turned into a hexidecimal or something so that it does not match what the router has as the pass phrase. What should I do now?

---

