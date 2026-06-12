---
title: "samsung nc10 Ubuntu 9.04 change mac"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by mrbigben on 2009-04-25
Hi all,

I just installed ubuntu 9.04 on my samsung nc10 and I need to change my wlan mac address in order to connect to the internet. I tried everything from "ifconfig" to "dhclient" and "macchange" but when i change my mac i cant connect to AP (no problems with the same changed mac using windows). Maybe someone could check if they can connect to their ap with changed mac. 				

Thanks.

---

### Post by coffeecat on 2009-04-25
Why specifically do you need to change your wlan MAC address?

---

### Post by ibuclaw on 2009-04-25
You can list your current Network Card MAC address by typing in:
```
ifconfig
```
in the commandline.

You will see something similar to this:
> 
eth0      Link encap:Ethernet  **HWaddr 00:1d:72:4f:58:70**  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

The HWaddress is the MAC address for that card.

How to change it can be found here: [http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/)

> **coffeecat said:**
> Why specifically do you need to change your wlan MAC address?
For about a week, I used MAC filtering on my router ... I chose to manually configure all computer MAC addresses so I knew for sure which one was which.
If one of those computers changed its address for some unknown reasons, it would be refused connection, let alone a passphrase.

I have given up on that sort of security for obvious reasons ...

Regards
Iain

---

