---
title: "Network stops when on static but restarts when on DHCP"
date: 2011-11-30
forum: Networking &amp; Wireless
---

### Post by Gizim on 2011-11-30
Running Ubuntu Server 11.10 doing a small Wiki for my work we have two interfaces eth0 (internal) and eth1 (external) I set the eth0 to DHCP pull whatever IP and then reserve that IP from our DHCP server. I set it to static ifconfig eth0 10.241.131.76 netmask 255.255.255.0 and set the external to our IP and everything works like a champ. Until I reboot the box when that happens i lose ALL connection I can't ping internal or external or ping out at all. I have to dhclient eth0 and when I do that traffic on BOTH interfaces starts flowing... and i have not a damn clue why?
Also about an hour ago I could ifconfig eth1 down and turn off the external to stop it from being on the internet to do some updates and to secure ssh/ftp/apache and all but now when i bring it offline i can still ping and remote in from external..
Thoughts?

---

### Post by jonobr on 2011-11-30
Could you post results of
/etc/network/interface
and ifconfig before and after the restart.

Also dmesg | grep eth may show something of interest ebfore and after restart also

---

### Post by Gizim on 2011-11-30
> **jonobr said:**
> Could you post results of
/etc/network/interface
and ifconfig before and after the restart.

Also dmesg | grep eth may show something of interest ebfore and after restart also

Sure thing - Not sure why eth1 is not in here, could that be why?

cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0
iface lo inet loopback

# The primary network interface
iface eth0 inet static
        address 10.241.130.76
        netmask 255.255.255.0
        broadcast 10.241.130.255
        network 10.241.130.0


BEFORE restart

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:56:b2:00:05
          inet addr:10.241.130.76  Bcast:10.241.130.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:feb2:5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18967 errors:0 dropped:132 overruns:0 frame:0
          TX packets:2233 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1580682 (1.5 MB)  TX bytes:1072311 (1.0 MB)

eth1      Link encap:Ethernet  HWaddr 00:50:56:b2:00:07
          inet addr:70.43.59.198  Bcast:70.43.59.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:feb2:7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10915 (10.9 KB)  TX bytes:936 (936.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:305 errors:0 dropped:0 overruns:0 frame:0
          TX packets:305 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:95155 (95.1 KB)  TX bytes:95155 (95.1 KB)



astracener@wiki:~$ dmesg | grep eth
[    3.045970] e1000 0000:02:00.0: eth0: (PCI:66MHz:32-bit) 00:50:56:b2:00:05
[    3.046173] e1000 0000:02:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    3.432937] e1000 0000:02:01.0: eth1: (PCI:66MHz:32-bit) 00:50:56:b2:00:07
[    3.433137] e1000 0000:02:01.0: eth1: Intel(R) PRO/1000 Network Connection
[   11.442964] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   21.892647] eth0: no IPv6 routers present
[  512.231302] e1000: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[  512.234703] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  512.235714] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  522.857214] eth1: no IPv6 routers present
[  882.679342] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[  882.683649] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  882.683958] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  893.252878] eth0: no IPv6 routers present
[ 2487.033311] e1000: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[ 2487.034576] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 2487.034799] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 2497.518596] eth1: no IPv6 routers present


AFTER RESTART - Network down

Sorry the server is a VM and when the network is down i can't SSH in so i had to take pics of the console output.

[https://imgur.com/a/9GSYu](https://imgur.com/a/9GSYu) that is the SS for both again sorry

---

### Post by jonobr on 2011-11-30
Hello


Noticing that eth0 is defined in interfaces file but eth1 is not.

Thats weird as your interface gets an IP address as in ifconfig.

Makes me wonder are you using NM applet for setting a static IP address and configuration files for DHCP on ETH0?

When you use NM applet the configuration is not in the /etc/network/interfaces file, so again, are you doing both?

---

### Post by Gizim on 2011-11-30
> **jonobr said:**
> Hello


Noticing that eth0 is defined in interfaces file but eth1 is not.

Thats weird as your interface gets an IP address as in ifconfig.

Makes me wonder are you using NM applet for setting a static IP address and configuration files for DHCP on ETH0?

When you use NM applet the configuration is not in the /etc/network/interfaces file, so again, are you doing both?

Nope, this is Ubuntu Server all terminal

---

### Post by jonobr on 2011-11-30
Where is eth1 getting 70.43.59.198 from?

---

### Post by Gizim on 2011-11-30
> **jonobr said:**
> Where is eth1 getting 70.43.59.198 from?

Well I used Webmin to set that so maybe that is why?
What should i put in the interfaces to turn on eth1?
I need eth1 to have that ip address static as its the forward facing interface.

But why would BOTH be down until i enable dhcp on eth0?

---

### Post by jonobr on 2011-11-30
Im not really sure how your setup so I dont want to mess up your config.
I dont use webmin so I would only be worried about configuring the config files correctly,

I would remove 10.241.130.76 from the lan DHCP server scope

the config file I would set to 

```

#loopback
auto lo
iface lo inet loopback

# Primary Lan network interface
auto eth0
iface eth0 inet static
address 10.241.130.76
netmask 255.255.255.0
broadcast 10.241.130.255
network 10.241.130.0

#wan interface
auto eth1
iface eth0 inet static
address 70.43.59.198
netmask 255.255.255.0
broadcast 70.43.59.255
network 70.43.59.0

```

and not use dhclient at all...

---

### Post by Gizim on 2011-12-01
> **jonobr said:**
> Im not really sure how your setup so I dont want to mess up your config.
I dont use webmin so I would only be worried about configuring the config files correctly,

I would remove 10.241.130.76 from the lan DHCP server scope

the config file I would set to 

```

#loopback
auto lo
iface lo inet loopback

# Primary Lan network interface
auto eth0
iface eth0 inet static
address 10.241.130.76
netmask 255.255.255.0
broadcast 10.241.130.255
network 10.241.130.0

#wan interface
auto eth1
iface eth0 inet static
address 70.43.59.198
netmask 255.255.255.0
broadcast 70.43.59.255
network 70.43.59.0

```

and not use dhclient at all...

Okay, put that all in except in the WAN i put 
iface eth1 inet static instead of eth0 - is that correct?

After a restart the internal is still not pingable but the external is.

Here is some added netstat -rn
[http://pastebin.com/GCYjagvz](http://pastebin.com/GCYjagvz)

---

### Post by jonobr on 2011-12-01
Hello


In the config example I gave, It assumes both ETH0 and ETH1 are static.

I may have misread your post, but I recall you saying,
You set eth0 to dhcp , let it acquire and address./
Mark that address as used in DHCP and then statically configure it in eth0?

If thats so, what I was recommending was allocate an IP to ETH0 and mark it as used in DHCP.

You could also allocate in DHCP based on the mac address supplied,
Either way my understanding was you were doing a static IP allocation on ETH0..... correct?

---

