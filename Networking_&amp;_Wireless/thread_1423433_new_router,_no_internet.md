---
title: "new router, no internet"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by Laeys on 2010-03-06
So I am having this problem because I don't know anything about routers and I don't know anything about linux.

When I first upgraded to 9.10 the network manager wouldn't connect to my DSL so I used the pppoeconf ( I don't know what it does just that it works now).  
I got a netgear wireless router for my windows netbook and was able to set it up for that wirelessly, but ubuntu doesn't seem to acknowledge the router (wired).  I tried running ppoeconf again and it said something about there already being a pppoe process.

Could someone please help me out?

---

### Post by Iowan on 2010-03-07
> **Laeys said:**
> ...I got a netgear wireless router for my windows netbook and was able to set it up for that **wirelessly**, but ubuntu doesn't seem to acknowledge the router (**wired**).. Are you connecting to the router via wire or wireless?

---

### Post by Laeys on 2010-03-07
I am connected via wire

---

### Post by Charly85551 on 2010-03-07
So, if you are wired and unless you want more problems stick with it! Don't try to connect wireless at the same time. The network rules (IEEE...) don't allow parallel connections. Your PPPOE indicates that you don't have the router activated properly but that it is in a DSL-modem only mode. Normally the router should be set-up as the one handling the PPPOE-protocol and all the PC's are connected to the router as the network controller using it's DHCP-server function. That's the normal way but there are dozen of other options though!
Netgear has a pretty straight forward way of setting up the router. Make sure you know the IP-address of it and check your PC's ifconfig file to make sure there is a line saying:
gateway = above router's IP-address
good luck
charly85551

---

### Post by Laeys on 2010-03-07
Charly, thanks for helping, I can't say I understood everything you said, but here is my ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:0d:56:f1:06:2a  
          inet6 addr: fe80::20d:56ff:fef1:62a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:585 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:103192 (103.1 KB)  TX bytes:2348 (2.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

and it doesn't say gateway anywhere or the ip address of the router, which is 192.168.1.1
Any ideas what this means and what I should do?

---

### Post by Iowan on 2010-03-07
What's in */etc/network/interfaces*? If it has more than the definition lines for "lo" you may want to comment them out.
Is "auto eth0" set to connect automatically? Another thing to check - If the machine gets its IP address via DHCP, is the router configured as DHCP server - or does it use the modem as it's gateway?

---

### Post by Laeys on 2010-03-07
> **Iowan said:**
> What's in */etc/network/interfaces*? If it has more than the definition lines for "lo" you may want to comment them out.
Is "auto eth0" set to connect automatically? Another thing to check - If the machine gets its IP address via DHCP, is the router configured as DHCP server - or does it use the modem as it's gateway?

I am afraid I don't know how to check any of these things.  How do I find */etc/network/interfaces*? How do I check "auto eth0" and how do I know if the router gets its address via DHCP?  Sorry I'm a bit clueless.

---

### Post by Iowan on 2010-03-07
You *should* be able to see what's in */etc/network/interfaces* by using a terminal to enter:```
cat /etc/network/interfaces
```If you used Network Manager to configure the interface(s), you should be able to right-click the icon (upper right corner) and "edit connections".

---

### Post by Laeys on 2010-03-08
> **Iowan said:**
> You *should* be able to see what's in */etc/network/interfaces* by using a terminal to enter:```
cat /etc/network/interfaces
```If you used Network Manager to configure the interface(s), you should be able to right-click the icon (upper right corner) and "edit connections".

Part of the problem is that I *didn't* use Network Manager to configure anything because it wouldn't connect to my dsl, so I used pppoe-conf at someone else's suggestion.

Here is my */etc/network/interfaces*:
```
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual
```

How would I edit this file if I wanted to?

---

### Post by Iowan on 2010-03-08
> **Laeys said:**
> How would I edit this file if I wanted to? You can use the default editor:```
sudo -e /etc/network/interfaces
```My favorite - **nano**```
sudo nano /etc/network/interfaces
``` or a graphical editor:```
gksudo gedit /etc/network/interface
```

At one time, NM would ignore interfaces in */etc/network/interfaces* - apparently that has [changed]("http://ubuntuforums.org/showpost.php?p=8936490&postcount=23"). Dunno if you can simply [disable]("https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager") NM - or if it must be removed...

---

### Post by Laeys on 2010-03-08
I commented out everything in *etc/network/interfaces* except ```
auto lo
iface lo inet loopback
```
,reboot and now it works.
Thanks Iowan for your help.

---

