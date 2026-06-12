---
title: "Inspiron 6400 only connects with passwordless device."
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by minhaaj on 2010-09-23
I have just installed ubuntu 10.04 on dell inspiron 6400. It was really hard to get it to work in first place but after installing b43-fwcutter it worked. Now problem is that it only connects to my wireless router when i take away security off of it. It doesnt authenticate connection when i set up WPA or WEP security on it. I have no idea whats wrong. I am posting this through wired connection. It works with both passwordless and cord connection but as soon as i set password it doesnt get through.

I have tried both WPA and WEP security and it doesnt get into any of that. I would be really thankful if you can help me with that. 

this is my iwconfig screen

root@ubuntu:/home/minhaaj# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"beaver"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 82:3B:6F:96:37:23   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:C8D9-DE48-602D-FEBA-29BF-281E-EC
          Power Management:off
          
pan0      no wireless extensions

---

