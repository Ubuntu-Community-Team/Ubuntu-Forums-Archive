---
title: "Connecting machines to a hub"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by DLuton on 2010-12-22
So, I have this hub for connecting up to 8 computers. It's simple, I plug the cable modem to slot one and my computer into slot two. For some reason, it works perfectly for me but i cannot connect other computers to it, slots 3,4, etc. I have read that there is a way to change your IP to a networking IP, 192.168.1.100, for this to work. Does anyone know what I am trying to do? If so, please help!

---

### Post by spiky001 on 2010-12-22
Is it a **HUB** or a **ROUTER** they are different

---

### Post by DLuton on 2010-12-22
Multiport Micro Hub

---

### Post by spiky001 on 2010-12-22
I dont think yo can do that with a hub you need a router if I,m wrong some one will put me right, I use my hub after a pc, so pc connects to internet then to a hub then the other laptops connect to hub, I think it,s something to do with allocating ip addreses to different machines

---

### Post by Boondoklife on 2010-12-22
The only way this would work is if your modem supported giving out multiple IPs, or it is a modem/router.

You can use one of the computers as a router, but then that computer has to be on for the other to gain internet access. Really the best solution is to just use a router.

---

### Post by redmk2 on 2010-12-22
> **spiky001 said:**
> I dont think yo can do that with a hub you need a router if I,m wrong some one will put me right, I use my hub after a pc, so pc connects to internet then to a hub then the other laptops connect to hub, I think it,s something to do with allocating ip addreses to different machines

You can interconnect hosts (machines) on a LAN with a hub just as you can with a switch.  They both are layer two devices.  These devices can't route packets out of the LAN (i.e. to the internet).  He does need a router (layer3).

A hub is common connector of all the hosts.  A switch provides separate channels of communication.

As you say, the problem sounds like an IP addressing issue.

---

### Post by redmk2 on 2010-12-22
> **Boondoklife said:**
> The only way this would work is if your modem supported giving out multiple IPs, or it is a modem/router.

I'll bet the modem does support DHCP.  If not then any of the attached computers can serve as a DHCP server.  The modem only needs to serve as a gateway for the LAN.
> 
You can use one of the computers as a router, but then that computer has to be on for the other to gain internet access. Really the best solution is to just use a router.

True; the host with DHCP would have to be on whenever the LAN is active.  Or the OP can just assign static IP addresses to the hosts.  The hub is very old school (10 mbps).

---

### Post by redmk2 on 2010-12-22
> **DLuton said:**
> So, I have this hub for connecting up to 8 computers. It's simple, I plug the cable modem to slot one and my computer into slot two. For some reason, it works perfectly for me but i cannot connect other computers to it, slots 3,4, etc. I have read that there is a way to change your IP to a networking IP, 192.168.1.100, for this to work. Does anyone know what I am trying to do? If so, please help!

Do you have the manual for the cable modem?  What make and model is it?  The problem is probably an IP address issue.  All the hosts (computers) need to be in the came IP address range to communicate.

---

### Post by DLuton on 2010-12-22
It did not come with a manual. But, it is a Motorola. I have a D-Link router, and it does work, but the connection gets really slow, like dial up slow. This router never did that before. I used to have phone DSL then switched to cable for faster speeds. The only computer I have tried the hub with (besides mine)  was an Asus laptop, also with ubuntu 10.10, but i could not get the internet to work. After a few manual changes to the network settings, i did get the connection established, but still no internet.

And yes, the modem supports DHCP.

---

### Post by redmk2 on 2010-12-22
> **DLuton said:**
> It did not come with a manual. But, it is a Motorola. 
Do you have the model number?  Can you get to the admin page of the device?> 
I have a D-Link router, and it does work, but the connection gets really slow, like dial up slow. This router never did that before. 
The D-Link never did what?> 
I used to have phone DSL then switched to cable for faster speeds. 
Okay...> 
The only computer I have tried the hub with (besides mine)  was an Asus laptop, also with ubuntu 10.10, but i could not get the internet to work. After a few manual changes to the network settings, i did get the connection established, but still no internet.
Do you know the LAN IP address of the Motorola device?

What did you do to the network settings to establish the connections?  Can you post the output for the 2 Ubuntu hosts using this command? ```
config -a
```

---

