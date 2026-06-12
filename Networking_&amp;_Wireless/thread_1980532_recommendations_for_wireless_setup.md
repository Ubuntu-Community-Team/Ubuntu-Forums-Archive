---
title: "recommendations for wireless setup"
date: 2012-05-15
forum: Networking &amp; Wireless
---

### Post by badperson on 2012-05-15
Hi,
I have a desktop machine (dual boots win 7 and ubuntu) connected to a wireless router, that is connected to a wireless cable modem. (the router is connected to the modem via ethernet)

I'm thinking I can just scrap the wireless from my cable company, right? Also...what is the best home wireless network setup for speed? By that I mean a combo of ISP and wireless hardware > setup. 

BTW...I'm in the new york area. 
thanks!
bp

---

### Post by TBABill on 2012-05-15
I'm not sure what you mean by best setup for speed because it depends on how you connect to the router. It's directly connected via ethernet so you get max speed by default normally. From your  machine to the router depends on your device, the driver, etc. If the driver can push 802.11n then you will get the highest speed. If it's a b/g device it will be limited to those capabilities.
 
if you want, yes you can disconnect the wireless built into the cable company's modem and just use your router's wireless. That's just preference based on which is more capable and reliable.

---

### Post by badperson on 2012-05-18
thanks.
What hardware would you recommend? 
here's what I get from lshw:

> $ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: eth0
       version: 10
       serial: 00:1b:2f:2e:bb:8c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.2 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:19 ioport:d800(size=256) memory:f3fffc00-f3fffcff


Attached is a screenshot from tcptrack. Is that the best tool to use, and what should I be seeing there? 

thanks...sort of a network noob :)

---

### Post by chili555 on 2012-05-18
The hardware you've shown is wired ethernet, not wireless. If you have no wireless devices in your home, and you don't expect to have any soon, you can disable wireless capability in the ISP's cable modem and disable wireless capability in the router. Wired ethernet is generally faster, more reliable and more secure than wireless.

I would keep the router because they almost always include a firewall that makes your home network more secure. If you choose to retain wireless in the router, for visitors, for example, be certain to use the highest level of security WPA2-AES and a secure password.

If you have more questions, please post back.

---

### Post by badperson on 2012-05-18
Hi,
thanks. I should have stated the question more clearly. 
My set up is: 

desktop -> wireless router(via ethernet) -> cable modem (also via ethernet)

other devices connect to the network thru wireless; I use the security features mentioned above. 

Lately I have had some performance issues; internet connection being dropped, and what seems like slow performance. 

So my questions are:
[LIST]
[*]how to best determine how fast my internet connection is vs. how fast it could/should be (tcptrack?)
[*]what is the optimal setup balancing  security/speed. Is there better hardware I could use? 
[/LIST]

thanks!
bp

---

