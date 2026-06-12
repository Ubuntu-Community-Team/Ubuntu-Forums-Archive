---
title: "How to put wireless card in Monitor mode"
date: 2011-10-28
forum: Networking &amp; Wireless
---

### Post by mrgoodfox on 2011-10-28
I'm a 1 month old Ubuntu user and learning on a daily basis (mostly from searches on this forum). 

The latest article I was reading was talking about putting a wireless USB card in monitor mode. Isn't every wireless card by default in monitor mode. I would assume if its receiving signal from the router it's monitoring the wireless traffic around it. Isn't it?

If not, first how do you put a wireless adapter in monitor mode? 
Second, would it only pick up the wireless traffic from the router that it's connected to or would it pick up whatever wireless information is in the air?

---

### Post by ajgreeny on 2011-10-28
I have no idea what "monitor mode" is, nor what that article meant by suggesting it was needed.  A wireless card will normally monitor or scan all the wireless signals in its area, as long as it is able to work in ubuntu.  If your card is not picking up any signals it may need a driver installed.

Is your card working for you?  If it is then you need not worry any further.  If it is seeing your router's wireless signal but is not able to connect, tell us more about the wireless security setup and the adapter itself, ie the make etc etc.

---

### Post by jonobr on 2011-10-28
in addition to the below,
you can 'monitor' the packets going across that interface using a network sniffer like wireshark or tcpdump
or you can 'monitor' the status of the interface periodically 
by dmesg |grep wlan
you should see high level information on connection/disconnection association and so on.....

however  +1 with ajgreeny the question is a tad ambiguous

---

