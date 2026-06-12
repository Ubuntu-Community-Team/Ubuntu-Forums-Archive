---
title: "Problems connecting Wifi RTL8187 WPA"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by The_Reaper on 2009-11-02
I can't connect to my wireless network with ubuntu 9.10. Windows connects well with the network. I want to remove the windows partition. 

I installed the RTL8187 driver with ndiswrapper. (USB wireless card)

I removed network-manager because it doesn't detect any wireless network.

My wifi router is configured without DHCP, with static IP, WPA2 preshared key and MAC Address filtering.

I installed wicd and it detects my wifi network but it can't connect with network.

Firstly, I tested without dhcp. I configured wicd with the correct data (IP,Netmask, preshared-key, the same configuration data as windows xp). If i push the connect button, wicd says: "validating" and after some time a error message appears saying "can't connect with the net". If I configure the router and wicd with dhcp the validation is succesfull but when wicd tries to obtain IP a error message is showed "can't obtain IP address".

Can anybody help me please? I really want to use ubuntu and delete windows, but if wireless doesn't work I cant. 

Am I doing something wrong?

---

### Post by The_Reaper on 2009-11-03
Anybody can help me?

I saw a lot online tutorials and I configure all like tutorials, but doesn't connect. I can take some logs information if is necessary, but I don't know what information can be useful to detect the problem. Any Idea?

---

### Post by Royke on 2009-11-07
Hello Reaper,
It seems that the RTL8187 driver has trouble with some wlan devices like with my Netgear WG111v3. I have read somewhere that thare is a way to disable it and use ndis-wrapper for using windows driver. But i can not find it anymore. I hpe you will be able to fix it now, greetings

---

### Post by The_Reaper on 2009-11-20
> **Royke said:**
> Hello Reaper,
It seems that the RTL8187 driver has trouble with some wlan devices like with my Netgear WG111v3. I have read somewhere that thare is a way to disable it and use ndis-wrapper for using windows driver. But i can not find it anymore. I hpe you will be able to fix it now, greetings

I'm using ndiswrapper.
I've returned to windows. I tried to resolve the problem doing a lot of different solutions but the problem persist.

---

