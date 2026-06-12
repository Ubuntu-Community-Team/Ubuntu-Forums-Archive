---
title: "no network connection"
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by dddkiran on 2010-08-21
Hi Guys!
I a trying to setup a wired connection in my ubuntu machine 8.04. but could not able to connect to internet, the internet status icon in status bar is always disabled irrespective of whether i connect the cable or not.

please help me!!!

Regards,
kiran

---

### Post by silbak04 on 2010-08-21
what is your output when you type this in the terminal ```
$ cat /etc/network/interfaces 
``` it should look some thing like this ```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.xxx
netmask 255.255.255.x
gateway 192.168.1.x 
``` where 'x' is some number according your ip address, netmask, and gateway...typically you want your ip to be static...especially when down the  road you may want to ssh into your computer from work or something...you  don't want to have an ip that always changes, which is what dhcp  does...

then type this in the terminal after fixing up your 'interfaces' file ```
$ sudo /etc/init.d/networking restart
```

---

### Post by dddkiran on 2010-08-21
!

I tried it, when restart iam getting error message like "failed to bring up eth0"

my interface file is like below:
#############
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 1.23.8.123
netmask 255.255.240.0
gateway 1.23.8.5

Regards,
kiran

---

### Post by Nick Kruger on 2010-08-21
I'm a complete beginner, but what I did was first use dhcp and have a careful look at the settings dhcp uses, then assign a static. I'm sure you were hoping for better advise than this.

---

### Post by silbak04 on 2010-08-21
This is for a wired connection (ethernet) correct? Not wireless? read me your output for ```
ifconfig
```

---

### Post by Iowan on 2010-08-21
**ifconfig -a** should "display  all  interfaces  which are currently available, even if down". To what does the machine connect - router, modem, another machine? Have you tried a different cable?

---

### Post by jaya28inside on 2010-08-23
loopback statement there,,, is it need to be removed?

:D

---

### Post by grahammechanical on 2010-08-23
Is your modem/router configured to connect to your ISP. I purchased my modem through my ISP. Actually it was free with the subscription. Therefore, information had already been entered by the ISP but I still needed to put in my ISP user name and password. So, the OS may not be at fault but the link between the modem and the ISP. 

Regards.

---

### Post by Confucius! on 2010-08-23
> **dddkiran said:**
> !
 
I tried it, when restart iam getting error message like "failed to bring up eth0"
 
my interface file is like below:
#############
auto lo
iface lo inet loopback
 
auto eth0
iface eth0 inet static
address 1.23.8.123
netmask 255.255.240.0
gateway 1.23.8.5
 
Regards,
kiran
 
 
Where did you get that IP address information from? That is not really a standard IP. Are you pluging your connection directly into the modem or into a router? If you are pluging it into a router do you know what ip info your router is giving out as DHCP leases. I would change it back to DHCP and then do a ipconfig. Then change it back to static and enter in the ip info you got from the DHCP lease.

---

### Post by Iowan on 2010-08-23
> **dddkiran said:**
>  the internet status icon in status bar is always disabled irrespective of whether i connect the cable or not. Be aware that interfaces defined in */etc/network/interfaces * are (or were) not generally managed by Network Manager. (Though early in Lucid's life, there were suggestions that NM had to be removed for "interfaces" file to work as it previously did).

---

