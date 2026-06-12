---
title: "Static IP setup"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by RedSingularity on 2009-06-06
How can i set a static IP in ubuntu 9.04?

---

### Post by puppywhacker on 2009-06-06
right click the little network icon on the right top next to the time and choose "edit connections". At the IPv4 tab change from automatic to manual and add the addresses/netmask/gateway below

The "old-school" method of editing /etc/network/interfaces will disable the network manager, and can be used for a more complicated setup

---

### Post by RedSingularity on 2009-06-07
Ok, now how can i do this to an IP address inside a Virtual Machine?

---

### Post by samuel1 on 2009-07-03
hi, im new to ubuntu. im using the same version of ubuntu 9.04
and im facing problems to put this work. I right click the network icon, put ipv4 to manual, insert my ip ,router
adress: 192.168.0.135
mask: 255.255.255.0
gateway: 192.168.0.1

what happens is that my connections go down at this moment
can anyone help me to put this thing work?
and how do i now my dns?


samuel@samuel-desktop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:23:54:16:7a:e7  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::223:54ff:fe16:7ae7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53613 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32828 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11638800 (11.6 MB)  TX bytes:124567283 (124.5 MB)
          Interrupt:250 Base address:0x6000 

samuel@samuel-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by computer13137 on 2009-07-03
> **Shadow121 said:**
> Ok, now how can i do this to an IP address inside a Virtual Machine?
Why would it be any different inside a virtual machine?  If you need to do it in a command line, simply edit your /etc/network/interfaces in your favorite text editor.  You can find information on how to do this here:
[http://codesnippets.joyent.com/posts/show/319](http://codesnippets.joyent.com/posts/show/319)

samuel1: Sorry, but your whole post doesn't make a lot of sense to me... go ahead and try reading the last page I posted.  [http://codesnippets.joyent.com/posts/show/319](http://codesnippets.joyent.com/posts/show/319)
What do you mean the connection "goes down"?  Are you still able to ping your router?  In the paste you gave us, the IP the interface has isn't the one you claim you set.  Additionally, why are you setting a static IP?  Does your router not have a DHCP server?  Also, I'm not understanding your question about DNS, please clarify that for me.

-Kirk

---

### Post by superprash2003 on 2009-07-03
did you try restarting networking after making changeS?
sudo /etc/init.d/networking restart

---

