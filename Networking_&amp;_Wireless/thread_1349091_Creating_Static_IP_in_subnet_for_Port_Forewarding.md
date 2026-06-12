---
title: "Creating Static IP in subnet for Port Forewarding"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by MadHatter21 on 2009-12-07
Hello,

I have a desktop running ubuntu server 9.10, I am trying to make a application i have made on it avilable on the internet but to do that I need to give it a static Ip address in my subnet. I have followed all of the tutorials on it but whenever i reboot and do a if config no eht0 is there with that static ip... amd i getting the information in the configuration file incorrect or what? help!!! 

Madhatter21

---

### Post by lloyd_b on 2009-12-08
> **MadHatter21 said:**
> Hello,

I have a desktop running ubuntu server 9.10, I am trying to make a application i have made on it avilable on the internet but to do that I need to give it a static Ip address in my subnet. I have followed all of the tutorials on it but whenever i reboot and do a if config no eht0 is there with that static ip... amd i getting the information in the configuration file incorrect or what? help!!! 

Madhatter21

Could you please tell us *what* "configuration file" you are modifying, and post the contents of that file?  It's hard to see what's wrong with something if you can't see it...

Lloyd B.

---

### Post by MadHatter21 on 2009-12-08
I am editing the interfaces file:

[FONT=monospace]
[/FONT]auto eth0
iface eth0 inet static
address 192.168.0.10
 netmask 255.255.255.0
 network 192.168.0.1
 broadcast 192.168.1.255
 gateway 192.168.1.1
But I am pretty sure i am not getting the correct info. Now eth0 is up but cannot resolve any websites and i is not because resolve.conf it is definetly the information above. How exactly do i get the information for each one of those. Just to let you know I would like the ip to be 192.168.0.10 and i have a router at 192.168.1.1 as well as my modem on 192.168.0.1, help

Madhatter21

---

### Post by lloyd_b on 2009-12-08
> **MadHatter21 said:**
> I am editing the interfaces file:

[FONT=monospace]
[/FONT]auto eth0
iface eth0 inet static
address 192.168.0.10
 netmask 255.255.255.0
 network 192.168.0.1
 broadcast 192.168.1.255
 gateway 192.168.1.1
But I am pretty sure i am not getting the correct info. Now eth0 is up but cannot resolve any websites and i is not because resolve.conf it is definetly the information above. How exactly do i get the information for each one of those. Just to let you know I would like the ip to be 192.168.0.10 and i have a router at 192.168.1.1 as well as my modem on 192.168.0.1, help

Madhatter21

You have a problem reaching your gateway.  With an IP of 192.168.0.10, and a netmask of 255.255.255.0, you can only reach other machines in the range 192.168.0.1 through 192.168.0.255.  But your gateway is at 192.168.**1**.1, which is outside that range.

To confirm this, "ping 192.168.1.1" in a terminal window, and see if it returns with "No route to host".  

Try changing the netmask to 255.255.254.0 - this will allow you access to the 192.168.1.x network via that interface, so it will be able to find the gateway.

(FYI - if your local network uses 192.168.1.x, it might just be simpler to assign that machine to an unused address on that subnet).

Lloyd B.

---

### Post by Iowan on 2009-12-08
> **lloyd_b said:**
> Try changing the netmask to 255.255.254.0 - this will allow you access to the 192.168.1.x network via that interface, so it will be able to find the gateway.Might make the 192.168.1.255 broadcast address kosher, too...

---

