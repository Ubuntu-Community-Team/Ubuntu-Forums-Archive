---
title: "Can connect but no internet Ubuntu 10.10"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by sparkzema on 2010-10-16
Ok, I had a fresh install of Ubuntu 10.10 after my backtrack 4 install stopped working.(bluetooth messed with hal or something mouse and keyboard wouldnt work) I plug my D-link G-122 (old laptop without built in wifi) and network manager recognized instantly. But whenever I connect to a network I can't get to the internet. It will connect and say its connected, but no internet. It's the exact same thing on my desktop. Any help is appreciated.

---

### Post by Iowan on 2010-10-17
Post results of:
**ifconfig -a**
**route -n**

---

### Post by QuantumLotus on 2010-11-07
I am having the same issue. Can connect to network, but not to internet. It should also be noted that I could previously but after installing a few programs it broke. I am a super green n00b and would appreciate any help..

---

### Post by QuantumLotus on 2010-11-07
Additionally a hard line connection does not fix this issue.. 

This may sound very silly but the things I installed were: search, frozen bubble, amarok, and the restricted ubuntu extras.

Working on getting those logs. As it is i'm typing all this on my phone.

Thanks

---

### Post by garvinrick4 on 2010-11-07
You do right click on applet on upper toolbar and enable and then check in edit connections
I am assuming?
 If so and nothing then use live Cd and see what happens if anyway possible give post 2 his
outputs he has been around a while and he will help you through this.

---

### Post by Def_101 on 2010-11-11
This worked for me.

[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

---

### Post by et1011 on 2010-11-14
I am having the same issue after a fresh install of 10.10.  The requested output is attached. Any help is much appreciated, thanks!

---

### Post by uncaspi on 2010-11-14
Try other nameservers i.e OpenDNS or google. ip 8.8.8.8
Click network icon select edit connections and tab ipv4 and put in the nameserver.

---

### Post by et1011 on 2010-11-14
Thanks uncaspi - I gave that a try using both    **8.8.8.8       8.8.4.4 **to no avail. After that I couldn't connect at all.

---

### Post by et1011 on 2010-11-14
I deleted the connection and re-added and presto, everything is working fine.  Thanks!

---

