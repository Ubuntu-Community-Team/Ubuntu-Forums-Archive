---
title: "How to get my wireless working again"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by razorboy5 on 2009-07-08
Hi again

I've been working on my wireless for about the whole day now and i think i'm getting very close

i used this tip

hit alt-f2 and type:
 [B]nm-applet --sm-disable

[/B]my wireless worked for a bit then i had to reboot my laptop. After which wireless no longer worked and even the alt-f2 then nm-applet--sm-disable did not even work either

so what does the nm-applet--sm-disable do anyways and why is my wireless not working anymore? 

anytips would be appretiated

thx

---

### Post by razorboy5 on 2009-07-08
more info
 
before when i was on Network Tools

one of the options under devices was wireless that no longer shows up

---

### Post by wojox on 2009-07-08
Why are you entering commands and then asking what they do?

Is there a Network Manager icon on your top panel.
If so right click
click edit

---

### Post by razorboy5 on 2009-07-08
not sure what u meant

i do not have a Network Manager icon however i have a Network Connections icon.

assuming those two are the same

before when i right clicked Network connections there used to be a "enable wireless" button however not anymore...;

---

### Post by t0mppa on 2009-07-08
Hitting Alt + F2 and running "nm-applet --sm-disable" simply starts up the applet in Network Manager that lets you decide which network to connect to. The --sm-disable part keeps it from loading up multiple sessions of the applet.

If you're not seeing wireless at all there, then you probably should check whether your drivers are working correctly and if you've just disabled the wireless with a button, which is a fairly common mistake for laptop users to do.

---

### Post by razorboy5 on 2009-07-08
sudo  lshw -C network

shows that my drives are working properly. Also wireless did work briefly so i dont think anything's wrong there

i just tried iwconfig

and got

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

on ifconfig

eth0      Link encap:Ethernet  HWaddr 00:03:25:4c:51:84  
          inet addr:192.168.0.36  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe4c:5184/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12714570 (12.7 MB)  TX bytes:2026062 (2.0 MB)
          Interrupt:250 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)




does any of that make any sense cuz it doesn't to me;;;

---

### Post by BScHamP on 2009-07-08
if you dont know what the commands do dont enter them, you could mess up your machine

refering to:

not sure what u meant

i do not have a Network Manager icon however i have a Network Connections icon.

assuming those two are the same

before when i right clicked Network connections there used to be a "enable wireless" button however not anymore...;

---

