---
title: "wired network and dhcp gets wrong ip"
date: 2010-12-25
forum: Networking &amp; Wireless
---

### Post by hiputuku on 2010-12-25
Hi, I have two os (windows and ubuntu) windows dhcp gets correct ip adress and enables the internet, but ubuntu doesn't. Where is a problem? Ip adresses depends only on MAC's address. Mac addresses are the same.

---

### Post by hiputuku on 2010-12-25
I forgot to say, that ipv4 is set to automatic in windows tool.

---

### Post by grahammechanical on 2010-12-25
If you right click the network icon and select Connection Information you can check to see if the primary DNS is the same as the Windows DNS servers.

If you select Edit Connections and select the IPV4 settings tab you can make sure that the Method is set to Automatic (DHCP)

An ethernet connection should get the correct information from the router/modem. It should not need to be set up. Not if Network Manager is installed. As I understand things the router/modem is a gateway. So, the Gateway Address is the IP address of the router/modem. This is how things look on my system.

Regards.

---

### Post by hiputuku on 2010-12-25
> **grahammechanical said:**
> If you right click the network icon and select Connection Information you can check to see if the primary DNS is the same as the Windows DNS servers.
You can see that primary DNS is the same.

---

### Post by gmargo on 2010-12-25
> **hiputuku said:**
> Ip adresses depends only on MAC's address.

Part of the DHCPDISCOVER packet is an optional field where the client can request a particular IP address, which the server will grant if possible.  So it is possible for Windows and Ubuntu to have different IP addresses with the same MAC address.

Is it your goal to force the two to have the same IP address?  One way to do that is to configure the DHCP server to force the assignment.  Another way could probably be devised to force the Ubuntu client to request the Windows IP address, after which they would always have the same IP.

---

### Post by hiputuku on 2010-12-25
> **gmargo said:**
> Another way could probably be devised to force the Ubuntu client to request the Windows IP address, after which they would always have the same IP.

Just added ip address directly into ipv4 settings,  dns netmask and gateway and My internet is online! Thanks for quick response! ;-)

---

