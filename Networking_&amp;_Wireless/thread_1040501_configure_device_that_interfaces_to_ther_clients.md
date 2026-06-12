---
title: "configure device that interfaces to ther clients"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by tednumber8 on 2009-01-15
Ok Im having a really confusing problem configuring IP, gateway and netmask

My router at the momnet has two devices connected, in the router settings 192.168.0.1 it shows that these devices are 192.168.0.2 nad 192.168.0.3.

I'm configuring the wireless network card so that it shares internet connection.

So far I've configured it like this 

> auto wlan0
        wireless-key 000000000
        wireless-channel 6
        wireless-mode ad-hoc
        wireless-essid 'wireless connection
        address 192.168.0.5
        gateway 192.168.0.4
        netmask 255.255.255.0'


eth0 is configured like this

> auto eth0
       iface eth0 inet dhcp


There is now a problem, there is no internet connection, what do I need to do to make this work properly?

I hope someone can show me, 3 weeks and counting, maybe ubuntu isn't so good after all

Is it to configure eth0 differently or can anyone help me configure these two so that they will work with firestarter for an ICS

---

