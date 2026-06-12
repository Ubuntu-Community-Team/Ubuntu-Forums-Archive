---
title: "Multiple NICs Ubuntu 8.10 64 bit"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by usafbran on 2009-05-15
Ok, my setup and intentions are pretty straight forward. Eth0 and Eth1 are onboard gigabit ports. I use Eth0 to connect to my modem through DHCP, and I use Eth1 to connect to my router which has a 48 port switch connected to it and 35 computers into the switch. My router is only 100mbit and i use the server for file sharing also. Obviously 1 gigabit is faster than 100mbit, so i purchased a PCI-E dual gigabit card with intentions of trunking it into my switch for the sole purpose of sharing files directly to the network. What i want to do is keep eth0 on the modem, eth1 to the router (I use tomato firmware for QoS) and i want to use eth2 and eth3 to plug directly into the gigabit switch bypassing the router for filesharing only. Everything works fine until i plug in the cables for eth2 and eth3, the server quits accessing the internet as it seems confused about which connection to use. I tried blocking access in the router to the MACs of the eth2 and eth3 so they wouldn't pull internet (creating a never ending loop in the server). I'm assuming the answer to this problem is as simple as fixing some routing issues in iptables, but I have no clue what to type in, nor was I able to find an answer specific to my problem - any help would be appreciated.
 
Yes, I know i could probably take the router out of the equation and use the server as a DHCP, but I know i can set this up how i have it already - i just don't know how.
 
Also, the server is running squid 3 proxy.

---

### Post by usafbran on 2009-05-15
I think my problem is NM is automatically trying to use the gigabit connection to the switch to access the internet since by default it's the "fastest" connection - thus creating a never ending loop to access the internet.  How do I make my server always pull internet through eth0 (100mbit connection to my modem) and not through eth2/3 (gigabit connection to the switch for filesharing)

---

### Post by usafbran on 2009-05-15
Ok - fixed my own problem.  Use this thread for your answer.
 
[http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

---

