---
title: "WPA2 on Ubuntu 9.04"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by sonymatteo on 2009-10-02
Hello,
I have a problem connecting to a wireless network in Ubuntu 9.04. 

The network I wish to connect is using WPA2, TKIP protocol, PEAP protocol and MS-CHAPv2 protocol. Network Manager is not able to connect, despite filling in correct username, password and certificate. I have also tried to install WICD instead of Network Manager, but the result was similar.

There is no problem connecting to any WEP network.

Thank you very much for help.

---

### Post by kingpoiuy on 2009-10-02
I've always had this problem too. Never really looked into it, just dealt with it. I'll be watching for replies!

---

### Post by peculiar penguin on 2009-10-02
My university uses a similar 802.1x setup (WPA2/AES/PEAPv0/EAP-MSCHAPv2) and NetworkManager connects fine... I just select the right SSID in the network list, feed it username/password/certificate and that's it.

Do you see anything odd in the logs?

---

