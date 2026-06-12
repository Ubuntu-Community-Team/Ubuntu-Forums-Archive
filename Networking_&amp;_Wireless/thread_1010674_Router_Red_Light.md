---
title: "Router Red Light?"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by ryanxmann on 2008-12-14
So I have just had to switch to using a router to broadcast internet to other computers in my house and I am having problems with it. Basically what goes wrong is that, sometimes when I have a strong signal on the modem and I am the only computer processing the connection it will go very slow and I noticed that at the back of my computer where I plug the ethernet cable into, is red on the inside, when the router is connected. But then when it's just direct wired connection from the modem it appears as a green light. I just would like some help to figure out exactly what the problem is, as I am somewhat new still to the WiFi network. I think I understand Linux fairly well and am getting very used to it. Here I list some of the settings I have with my router connected(I'm not sure if there is anything else that would help if I listed) :
root@ryan-desktop:/home/ryan# cat /etc/network/interfaces
auto lo
iface lo inet loopback

root@ryan-desktop:/home/ryan# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:76:ad:97:9d  
          inet addr:192.168.1.100  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:76993 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:3639 txqueuelen:100 
          RX bytes:35086349 (35.0 MB)  TX bytes:8417295 (8.4 MB)
          Memory:dfde0000-dfe00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30600 (30.6 KB)  TX bytes:30600 (30.6 KB)

pan0      Link encap:Ethernet  HWaddr 4a:f9:fc:2f:7f:74  
          inet6 addr: fe80::48f9:fcff:fe2f:7f74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:1836 (1.8 KB)


And the second computer that is on the network is able to connect wirelessly but also there are times when it gets very slow and doesn't work until we reset the router. And I don't know if it has any relation but I cannot connect my Palm TX through it either. My router is a LinkSyS WRT55AG and I use WPA-Personal(TKIP) as wireless security. 

Any help would be greatly appreciated. Thank you.

---

