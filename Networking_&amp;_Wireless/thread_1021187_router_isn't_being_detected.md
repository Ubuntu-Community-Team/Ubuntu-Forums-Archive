---
title: "router isn't being detected"
date: 2008-12-25
forum: Networking &amp; Wireless
---

### Post by JaysonL on 2008-12-25
this is driving me nuts. i just built my computer, installed 8.10 ubuntu and everything seems great. i hooked up my router, a 2wire 2701hg-b and my computer isn't detecting it. in the network manager drop down applet it says no available network device. all i can do from there is go in and set up vpn connections. i'm pretty brand new at this so i'm feeling more than a little frustrated with this. everything on the router indicates that everything's fine, internet, etc...i'm using it on our other computer in the living room (windows (this is my first experience with ubuntu)) my comp just won't recognize it. so please...guide me through to internet access! lol. thanks for the help in advance.

---

### Post by Iowan on 2008-12-26
> **JaysonL said:**
> ...in the network manager drop down applet it says no available network device. Sounds more like it's not finding the interface adapter than the router. Probably needs a different driver (which I won't be able to help with).  From a terminal, check **lspci** and/or **lshw**.  **ifconfig -a** might show something... You can also check contents of */etc/networking/interfaces*.

---

### Post by abn91c on 2008-12-26
in case you didnt already, power off PC, then the router. Then power on router, wait 30 seconds[COLOR="Red"] then[/COLOR] start computer. Also check the router manual on how to reset it. Also in a terminal you can try dhclient eth0

---

