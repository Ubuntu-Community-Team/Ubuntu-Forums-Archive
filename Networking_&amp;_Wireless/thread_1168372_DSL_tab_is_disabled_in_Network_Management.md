---
title: "DSL tab is disabled in Network Management"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by James4 on 2009-05-24
hey there,
since my first installation of kubuntu I haven't been able to go online.
in Interpid I wasn't able to set a username and password for my adsl connection and now in Jaunty the DSL tab is disabled.
here is a snapshot of the problem.
how can I fix this.
[img]http://img.piqlet.com/snapshot1.png[/img]

---

### Post by James4 on 2009-05-26
hey hey hey

---

### Post by superprash2003 on 2009-05-26
post output of ifconfig from the terminal

---

### Post by Dachlawine on 2009-05-26
same here. :-(

Here's the output of ifconfig

```
 eth0      Link encap:Ethernet  Hardware Adresse 00:1d:7d:d0:41:87
           inet6-Adresse: [fe80::21d:7dff:fed0:4187/64]("http://fe80::21d:7dff:fed0:4187/64") Gültigkeitsbereich:Verbindung
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
           Kollisionen:0 Sendewarteschlangenlänge:1000
           RX bytes:0 (0.0 B)  TX bytes:2178 (2.1 KB)
           Interrupt:251 Basisadresse:0x4000
 

 lo        Link encap:Lokale Schleife
           inet Adresse:127.0.0.1  Maske:255.0.0.0
           inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
           UP LOOPBACK RUNNING  MTU:16436  Metrik:1
           RX packets:56 errors:0 dropped:0 overruns:0 frame:0
           TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
           Kollisionen:0 Sendewarteschlangenlänge:0
           RX bytes:3528 (3.5 KB)  TX bytes:3528 (3.5 KB)
 
```

I'm sorry, but this is the german version. These translations might help you:
Gültigkeitsbereich = area of validity(?)
Verbindung = connection
Sendewarteschlangenlänge = length of sending queue

---

### Post by dmizer on 2009-05-26
Please post the contents of /etc/network/interfaces

---

### Post by Dachlawine on 2009-05-26
Loos like this:

```
auto lo
iface lo inet loopback
```

I didn't change anything in it, 'cause I'm a newbie. Does it matter whether I connect via a router or via broadband modem? I use the latter of 'em.

---

### Post by dmizer on 2009-05-26
Do you need to configure a PPPoE connection, or do you just want to connect via DHCP?

---

### Post by Dachlawine on 2009-05-26
If my provider configures DHCP automatically, that would be most appropriate. Otherwise I'd need a pppoe-connection (which I used under 8.04).
I simply want my machine to connect at startup.

---

### Post by dmizer on 2009-05-26
Try this:
```
sudo dhclient eth0
```

---

### Post by Dachlawine on 2009-05-26
ok, my system returns this:

```
 Listening on LPF/eth0/00:1d:7d:d0:41:87
 Sending on   LPF/eth0/00:1d:7d:d0:41:87
 Sending on   Socket/fallback
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
 No DHCPOFFERS received.
 No working leases in persistent database - sleeping.
 
```

---

### Post by Dachlawine on 2009-05-26
btw, I don't really think that there are any DHCP offers received as I'm not connected to my provider (because I don't have a router but a DSL modem). o.0

---

### Post by dmizer on 2009-05-26
Some modems also do routing.

Try this: [https://help.ubuntu.com/community/ADSLPPPoE#Configuring%20PPPoE%20with%20the%20command%20line](https://help.ubuntu.com/community/ADSLPPPoE#Configuring%20PPPoE%20with%20the%20command%20line)

---

### Post by Dachlawine on 2009-05-26
that somehow looks familiar to me ;)
Is there a way to integrate the "pon" command in the system startup?

EDIT: just found the chapter "boot issues".

Thanks in advance

---

### Post by Iowan on 2009-05-26
This looks painfully familiar:[http://ubuntuforums.org/showthread.php?t=1156441]("http://ubuntuforums.org/showthread.php?t=1156441")
My DSL modem handles the PPPOE configuration.  It has several "router-type" functions - a DHCP server (which I bypassed), port forwarding, firewall, etc.
My (Breezy) DHCP server apparently doesn't know what to do with rfc3442,  so disabling the request in */etc/dhcp3/dhclient.conf* fixed the problem for now.

---

### Post by Dachlawine on 2009-05-26
dmizer,

ev'rything works just perfect. THANK YOU! :)

---

### Post by dmizer on 2009-05-26
> **Dachlawine said:**
> dmizer,

ev'rything works just perfect. THANK YOU! :)

Well, at least you're online, but network-manager should have worked for you. I highly suggest following and contributing to this bug report: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/368709](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/368709) (Thanks Iowan).

---

### Post by James4 on 2009-05-27
but my problem still persists.
I don't wanna use the pppoeconf command cuz there will be some compatibility issues with gnome network manager which is working just fine.
I just want my DSL tab to be activated.

---

### Post by dmizer on 2009-05-27
I found a bug on this: [https://bugs.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/339882](https://bugs.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/339882) you should add comments and contribute information, particularly that the problem persists in the current release.

---

### Post by kruisa7 on 2009-06-04
I have the same problem in Kubuntu.  Network Manager seems good for dhcp and some wireless, but it doesn't handle much more very well.  With Ubuntu I added one package and then the network manager was able to set up a new dsl connection.

Advice varies, but you will need to use pppoeconf in a terminal to get the connection working.  My problem is that each time I log in it won't start, and I need to use pppoeconf.  All of the other possibilities such as pon dsl-provider, pppd call dsl-provider fail.  I'm happy that I have a connection, but not happy because with Ubuntu I can connect by clicking on the network manager icon in the task bar and the name of the connection, but with Kubuntu - no such possibility, unless I have a simple dhcp connection (which I don't).  Even worse, other distros do it so much better.

---

