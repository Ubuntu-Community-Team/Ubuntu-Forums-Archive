---
title: "share ubuntu internet connection with vista"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by huffmonster on 2009-07-01
I have ubuntu 9.04 on my laptop. i have a desktop running vista x64. my ubuntu laptop connects to the internet thru wifi, and would like to share the internet connection with my vista desktop thru a wired connection such as ethernet or crossover cable, how do i do this? i would rather not shell out $50 for a crap usb wifi adapter when i already have both ethernet and cross over cables in my posession. also i live in a house divided up into 4 apts that share the wifi, i do not have direct access to the router thats why i need to share my laptops connection with the desktop, can anybody help me out?? thanks :)

---

### Post by biyouboogie on 2009-07-01
Well friend, the way you do that is to turn the PC that is WiFi connected, and has an open Ethernet port into a ROUTER.   I suggest that you read the "How to turn on routing" section of the help files on which ever PC is doing the WiFi connection.   It's going to slow down the performance of your PC running the ROUTING protocol.  If you're not transferring a LOT of data then it should not be too bad.   If you're a POWER DOWNLOADER then it's going to be somewhat of a performance hit to the routing PC.  I think you said the WiFi is on your Ubuntu PC.   Do a search for Routed or Gated and read the "how to".   As for the cable, I think you'll need a crossover cable to link the two together since Hubs and Switches and Routers and Bridges do the crossover for you.

Good luck with it all.

Some details below:

Gated (gateway daemon) turns your PC into a Gateway
Routed (route daemon) turns your PC into a Router
They are similar, but not exactly the same.  Do some online reading before deciding which you will be doing.

Also, if you're going to use the Ubuntu system to provide the IP address to the Windows Vista system, you also need to make the Ubuntu system the DHCP server.   Read up on that too.  Otherwise, read up on how to manually give your Ethernet port on the Ubuntu system a specific IP address.  This is not rocket science, but it is "touchy" when setting up.   WAY too much detail to reply to here.  RTFM for more information.  :)  Basically you're going to have 2 totally different network subnets.

e.g. 192.168.1.x on your WiFi port  (local intranet)
     10.10.10.x on your Ethernet port.   (another local intranet)

Now the 2 networks have to communicate, and the hard part is that 192.168.x.x is NEVER routed past your router.   The packets that leave the PC headed out of the WiFi router are given a new IP address in the router.  This keeps your IntRAnet address from being seen in the IntERnet.   They figured this out early in the "networking" discussions and knew that PRIVATE NETWORKS had to be hidden from the Internet.

biyouboogie

---

### Post by biyouboogie on 2009-07-01
OR.....
get a damn wireless card for the Windows PC.   Nuff said.

---

### Post by huffmonster on 2009-07-14
> **biyouboogie said:**
> OR.....
get a damn wireless card for the Windows PC.   Nuff said.

OR...
dont be such an ***

maybe i dont wanna spend money on something i dont have to.

---

### Post by martinbaselier on 2009-07-15
One tip: I've found that the network manager gives some conflicts when running a dhcp server. So you probably need to disable or remove it and setup your network manually.

For setting up your laptop as a router, there are quite a lot good tutorials on the net.

---

### Post by superprash2003 on 2009-07-15
have you tried firestarter? they have an ICS feature

---

