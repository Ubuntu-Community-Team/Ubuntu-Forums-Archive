---
title: "ubuntu 10.04 (ics) sharing with xbox 360"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by Cjtouhey on 2010-05-18
Hey ive got my laptop hindered up to my xbox 360 it has windows 7 and Ubuntu 10.04. i realy want to get rid of windows and the only reason i keep it around is because ics sharing works realy well for connecting to xbox live. 
 
i recently discovered that you can (ics) with ubuntu which is awesome only problem is 
i cant figure out how to set it up to stop it having moderate NAT so i can play games that require an open NAT. its probably due to the ports not being fowarded properly or somthing and/or the face that my xbox needs a static ip placed out side the routers firewall on the DMZ setting 
 
can some one help me youle be helping me get rid of the pain and bother that is microsoft windows. 2 things i have to add i can use command line but i dont like to use it unless absoultly nessecery i get confused when trying to setup networks with it, and two who ever helps me is awesome forever :D
 
cheers from chris

---

### Post by brayden551 on 2010-05-18
The reason why I have Moderate NAT on my Xbox360 is because of my dns or my Internet. Now I looked into Port Fowarding and I cant find the xbox live option >.< There used to be certain game settings on my router- but cant find them..  As far as I know, you cant connect ubuntu to xbox- unless you like trick xbox 360 or something. lol. Did you try unplugging your router and modem and waiting 30 seconds? Try that.

---

### Post by Cjtouhey on 2010-05-18
> **brayden551 said:**
> The reason why I have Moderate NAT on my Xbox360 is because of my dns or my Internet. Now I looked into Port Forwarding and I cant find the xbox live option >.< There used to be certain game settings on my router- but cant find them..  As far as I know, you cant connect ubuntu to xbox- unless you like trick xbox 360 or something. lol. Did you try unplugging your router and modem and waiting 30 seconds? Try that.

Port forwarding is done on your router, and your firewall you need to forward the ports on both. log into to your router and go to port forwarding the ports that need to be opened are listed on xboxs customer suport page, also you need to set your xbox 360 outside your routers firewall using the DMZ game setting some routers dont have this. i just need to know how i can do this using Uubntus (ICS) seeing as i got an Moderate NAT cause i have no idea how i can foward the ports on it when the xbox 360s ip adress is weird, usaly on windows my ip adress is very simular ill assign a static ip adress of 192.168.1.107 to the xbox then just set that outside the router but the ics on ubuntu is completly diffrent if only there was a way to bridge conections easily on ubuntu

---

### Post by LoneTonberry on 2011-01-18
I got the moderate NAT issue to go away by doing a few things. First of which was using iptables to forward ports 80, 88, 53 and 3074 to my wireless connection. If the Xbox will connect to the internet fine using the Windows ICS (Like mine did) Either this or installing the linux-igd package and running upnpd wlan0 eth0 where wlan0 is your wireless card and eth0 is the Ethernet interface connected to the Xbox.

---

### Post by Im_taylor_made_ on 2011-01-28
What if your using an ethernet cable to connect xbox to laptop AND using cricket mobile broadband as your internet service?  It worked on windows xp

---

