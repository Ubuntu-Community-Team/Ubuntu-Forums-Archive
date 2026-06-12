---
title: "my NDIS commands don't work in Dapper"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by goneskiing on 2006-07-03
My hard wire eth0 works fine but I cannot get wireless working

In Breezy I typed in:
sudo modprobe ndiswrapper
sudo iwlist wlan0 scan
sudo iwconfig wlan0 essid <....>
sudo dhclient wlan0

Now in Dapper this doesn't work.  I realize under Dapper we don't need ndiswrapper anymore but I don't understand how to get my wireless configured.  I see under System|Admin|Networking that I can type in the essid and activate eth1 but how do I scan to get the available essid's ?  Any help appreciated.  ps  I have a Dell Inspiron 5150 with built in Broadcom wireless.

---

### Post by stupidkid on 2006-07-03
iwlist wlan0 scan 

This will get you available essids.

---

### Post by goneskiing on 2006-07-03
Notice that I had that command in my old list - that command gives me an error in Dapper

---

