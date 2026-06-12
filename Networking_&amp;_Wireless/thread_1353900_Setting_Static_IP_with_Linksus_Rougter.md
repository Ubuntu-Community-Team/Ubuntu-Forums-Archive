---
title: "Setting Static IP with Linksus Rougter"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by Wolfpup on 2009-12-13
[FONT=Times New Roman][SIZE=3]I am in the process if setting up a file server and wish to be able to remote access it through the Internet. i will be also be setting up an account with dyndsn so that i can acess my network from any where via a simple web address as my isp is dynamic addressing. but im having difficulties getting my file server set to a static ip on my local network and still be able to access the net with is as i get videos via bit torrents. when i goto set the static ip in the system viat the desktops network manager i loose all connection to the system as i do everthing via remote desktop and then have to goto that actually computer and reset everything so that it can be accessed again. i need to know what numbers i need to get and where to put them so that it will work right and when i have the more HDD's added to the system i will be adding xampp to have a locally stored web page.[/SIZE][/FONT]

---

### Post by Iowan on 2009-12-13
In case I'm misunderstanding something...
From your title, it sounds like you want to configure a static IP (static lease?) for your server on the Linksys router. That would mean leaving the server configured to get DHCP address (It'd just always be the same one).

Or... did you want to configure static address on the server? BTW, I presume you're either using a desktop as a server, or installed a desktop on the  server version (since servers generally don't have Network Manager).

I like the static lease option (some consider it overly complicated and overkill for small network). I'm not familiar with all versions of Linksys, but if you'd mention your model #, I'll try to help set up a static lease. The static lease address will need to be outside the DHCP lease range.

---

### Post by Wolfpup on 2009-12-14
ye i have a desk top computer running the desktop version of ubuntu and
 i want it it have a static ip on the local network so when i set up port
 forwarding i can set to to that system. i am in the process of setting up an
 account and free domain with dyndns so that i can hae remote access to
 my system from any where useing the free vnc viewer like i do on my local
 network. as well as setting up a web site and all.

---

### Post by megamania on 2009-12-14
> **Wolfpup said:**
> ye i have a desk top computer running the desktop version of ubuntu and
 i want it it have a static ip on the local network 
As far as I know, all you have to do is set the static ip address on the computer - nothing needs to be done on the router.

I can't be more specific right now because I'm not at home, but once you set the static ip address on the computer and restart the service everything should be ok.

---

### Post by Wolfpup on 2009-12-14
> **megamania said:**
> As far as I know, all you have to do is set the static ip address on the computer - nothing needs to be done on the router.

I can't be more specific right now because I'm not at home, but once you set the static ip address on the computer and restart the service everything should be ok.

that is my problem when i set a static on the computer it looses all connection to the internet and i even loose remote acess to the system on my local network

---

### Post by megamania on 2009-12-14
> **Wolfpup said:**
> that is my problem when i set a static on the computer it looses all connection to the internet and i even loose remote acess to the system on my local network
What's the local ip address you have now, and what static address are you trying to set up?

And what procedure did you follow to setup the static ip address on the computer?

---

### Post by Wolfpup on 2009-12-14
> **megamania said:**
> What's the local ip address you have now, and what static address are you trying to set up?

And what procedure did you follow to setup the static ip address on the computer?
the local ip is set buy my linsys roughter and was trying to set the ip4v setting under edit connections for my network intrface. the roughter sets the local ip adress to 198.168.1.XXX with a net mask of 255.255.255.0 but the my isp has a different net mask. to get to the edit i right click on the network icon in the taskpnl and slect edit connections the click the auto eht0 and click edit. then click ip4v tab.

---

### Post by shairozan on 2009-12-14
Hey, 

If you're losing connection to the internet, it's probably because you've forgotten to add the default gateway. When looking at the settings for the interface in control panel, as you are already doing, you will notice there are three things it wants

(1) Address (192.168.1.xxx)
(2) Netmask (255.255.255.0 for a Class C network such as yours)
(3) Gateway (192.168.1.1 more than likely)

Try setting the address with the gateway of 192.168.1.1 and then save. Once you have done that, re-initialize the connection by clicking on the network manager icon and click on your connection (more than likely auth eth0). 

Hopefully this will solve your problem. Also, once you have statically set your address, don't forget to remove that address from the DHCP pool on the router, otherwise something else will get that address eventually and you will have an IP conflict.

---

### Post by Iowan on 2009-12-14
Hopefully, you're setting a static address in the same subnet as the DHCP server issues - not the one you get from ISP (that'd also cause an immediate problem). 

If you happen to know what the address range is for the DHCP server, pick one outside the range - but still in the subnet. For example, if the DHCP server issues addresses from 192.168.1.100 - 192.168.1.200 with 255.255.255.0 subnet mask, you could use 192.168.1.201 (or any number between 201 and 254). You'll also want to avoid using the router/DHCP server address, too...

---

### Post by Wolfpup on 2009-12-15
> **shairozan said:**
> Hey, 

If you're losing connection to the internet, it's probably because you've forgotten to add the default gateway. When looking at the settings for the interface in control panel, as you are already doing, you will notice there are three things it wants

(1) Address (192.168.1.xxx)
(2) Netmask (255.255.255.0 for a Class C network such as yours)
(3) Gateway (192.168.1.1 more than likely)

Try setting the address with the gateway of 192.168.1.1 and then save. Once you have done that, re-initialize the connection by clicking on the network manager icon and click on your connection (more than likely auth eth0). 

Hopefully this will solve your problem. Also, once you have statically set your address, don't forget to remove that address from the DHCP pool on the router, otherwise something else will get that address eventually and you will have an IP conflict.
i tried the steps you listes and my ubuntu system gets imdiatley locked off the internet.
 after making the adjustments. i reset the the net connection and then open Firefox and
 try to goto a web page ad it will say server not found.

---

