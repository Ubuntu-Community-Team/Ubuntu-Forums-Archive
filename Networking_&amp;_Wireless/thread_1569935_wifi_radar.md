---
title: "wifi radar"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by ANew on 2010-09-07
Is there a way to see the manufacture of wifi router/card
remotely like "inSSider" shows, for example ???

---

### Post by ANew on 2010-09-09
Nobody replied :(

---

### Post by BkkBonanza on 2010-09-09
The manufacturer is determined by the first 3 numbers in the MAC address.
eg.  00:0C:41 Cisco-LinkSys

[http://anonsvn.wireshark.org/wireshark/trunk/manuf](http://anonsvn.wireshark.org/wireshark/trunk/manuf)

On Linux you can use Kismet for passive scans. 
And Wireshark but I don't recall if it decodes the MAC or not.

---

