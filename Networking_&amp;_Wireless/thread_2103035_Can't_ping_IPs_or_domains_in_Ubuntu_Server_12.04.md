---
title: "Can't ping IPs or domains in Ubuntu Server 12.04"
date: 2013-01-09
forum: Networking &amp; Wireless
---

### Post by TBBucs on 2013-01-09
On server...
ping 127.0.0.1 works
ping 192.168.1.104 (server's static IP address) works
ping google.com does not work (unknown host google.com)
ping 8.8.8.8 does not work (destination host unreachable)
ping 192.168.1.147 (local network machine's IP address) does not work (destination host unreachable)
ping 192.168.1.1 (router) does not work (destination host unreachable)

On local network machine...
ping 192.168.1.104 works

/etc/network/interfaces

[INDENT]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.104
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1[/INDENT]

/etc/resolv.conf

[INDENT]nameserver 192.168.1.1[/INDENT]

Any idea what's going on here?

---

### Post by subco on 2013-01-09
1- check out "iptables" 
2- ping 192.168.1.1 and 192.168.1.47 and then check "ARP Cache Table" with command 
```
arp -n
```

---

### Post by TBBucs on 2013-01-09
iptables -L says lists the policy for INPUT, FORWARD, and OUTPUT as ACCEPT.

arp -n lists both of the IPs I tried to ping and says that the HWaddress is incomplete.

---

### Post by sanderj on 2013-01-09
On the server, what's the out of 'ifconfig'? Post it here.

And is the ethernet cable connected at all?

---

### Post by TBBucs on 2013-01-09
I feel like an idiot. Turns out the ethernet cable was slightly loose. But I'm still not out of the woods just yet. I can now ping Google's IP (8.8.8.8), but ping google.com gives me an unknown host error. I can ping my router and local network computer successfully, and my network computer can ping my server as well.

---

### Post by sanderj on 2013-01-09
> **TBBucs said:**
> I feel like an idiot. Turns out the ethernet cable was slightly loose. But I'm still not out of the woods just yet. I can now ping Google's IP (8.8.8.8), but ping google.com gives me an unknown host error. I can ping my router and local network computer successfully, and my network computer can ping my server as well.

That means your name resolving is not working. 

How did your server get its IP address? Via DHCP, or ... ?

---

### Post by TBBucs on 2013-01-09
The server gets a static IP address of 192.168.1.104.

---

### Post by sanderj on 2013-01-09
> **TBBucs said:**
> The server gets a static IP address of 192.168.1.104.

Gets via DHCP, or sets via static config ... ?

---

### Post by TBBucs on 2013-01-09
Via static config.

---

### Post by Cheesemill on 2013-01-09
From 12.04 onwards you shouldn't edit resolv.conf directly as it gets rewritten by the system. Instead you should add the following line to your /etc/network/interfaces file:
```
auto eth0
iface eth0 inet static
address 192.168.1.104
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
[COLOR=Red]dns-nameservers 192.168.1.1[/COLOR]
```

---

### Post by TBBucs on 2013-01-09
Ah, adding the dns-nameservers line did the trick.

Now the issue is that I can't access the server from my Windows machines through the GUI. Navigating to \\192.168.1.104 in Explorer gives me a "Windows cannot access 192.168.1.104" error. That would suggest that the server isn't allowing connections from other machines, but how do I go about changing that in Ubuntu Server (note that I don't have a firewall enabled on the server yet, so that's not the issue)?

---

### Post by TBBucs on 2013-01-09
Fixed the Explorer problem. I needed to reconfigure my Samba share, as it got messed up during my reinstall of Ubuntu Server. I can now access the sever through the Windows GUI, as well as SSH into the server.

Thanks for your help everybody!

---

### Post by Cheesemill on 2013-01-09
Do you have any services running on the server to connect to?

For example to access shared drives from a Windows machine you would need to install and configure Samba on your server...
[https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html)

---

