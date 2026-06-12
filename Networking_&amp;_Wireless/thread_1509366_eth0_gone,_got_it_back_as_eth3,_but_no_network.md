---
title: "eth0 gone, got it back as eth3, but no network"
date: 2010-06-14
forum: Networking &amp; Wireless
---

### Post by kuckie on 2010-06-14
Hi there,

yesterday without reason my eth0 dissappeared. I read through various threads, tried couple of things, and now it´ s back as eth3. If I bring up the network on the console it says [OK], but I cant ping my router or access any website.

BTW:
During the proccess I removed network-manager-kde, which I regret now (cause I cant install it again w/o network). Even so my network was configured manually, it would be good to have it now for testing connections. The machine also got no CDROM-drive, I installed via USB.

All help´ s appreciated!

EDIT: I booted up again, and now eth3 is gone again 
I get the former error message when I restart the network: "eth3: ERROR while getting interface flags: No such device"
Same with all other ethX.

As far as I can see w/ my basic knowledge, the realtek adapter is present and working.

ifconfig only shows me "lo" nothing else.

I cant post copied output, as the machine got no network and I have to walk across the room to type it on my other computer...

---

### Post by Peter09 on 2010-06-14
Check the lights on your ethernet card and also the switch port that the card is connected to. It could have been a faulty card or the ethernet cable. Might be more complex now, depending on what you have done.

---

### Post by kuckie on 2010-06-14
Ok here ´s an update:

The device is back as eth1. Light on the ethernet-card (onboard) is on, if the cable is plugged in. I tried two different cables, checked connections and reseted the switch, same with the router. 

If I restart the network from the console with dhcp-settings, it starts looking for a dchp-broadcast, gives up after trying severel ports and then dies with [OK]. If I use manual IP-configuration (the one that was working before) it also dies with [OK] and no further messages. Either way the problem remains, I cant even reach the router by it´s IP-adress.

EDIT: Switch and router are working, I surf with this machine from the same network.

---

### Post by kuckie on 2010-06-14
> **Peter09 said:**
> . Might be more complex now, depending on what you have done.

Oh I forgott: What I did before was only editing /etc/network/interfaces changing the device name from eth0 to eth1,2,3... and switching between static IP and dhcp, and restarting the network over and over again, also rebooting couple of times.

I didnt mess with drivers, modprobe or alike.

---

### Post by Peter09 on 2010-06-14
can you show the output of
 
```
ifconfig
```
and
```
lshw -C network
```

---

### Post by kuckie on 2010-06-14
As I said I can´t copy the output, I try to describe best I can.

```
ifconfig
Output:
eth1: description looks "normal", got even the correct IP addresses if I use a static config as described above, interresting are the 800 dropped packages.

lo: looks normal to me..

```

```
lshw -C network
Output starts with:
*-network
description: Ethernet interface
product: Name of the realtek adapter
...at least 10 lines of description, looks normal to me, no errors or alike

```

EDIT: I´m about to leave here, if it´s still necessary I will search for an usb-stick and copy the output to a text file, when I get back.

---

### Post by Peter09 on 2010-06-14
If you use the command like this
 
```
ifconfig > ~/Desktop/ifconfig.txt
```
 
the output of ifconfig will be put into a file on your Desktop called ifconfig.txt. You can put the output of any command into a file by using the '>' sign. Perhaps you could the transfer it to your other machine via a usb drive.

---

### Post by kuckie on 2010-06-14
here we go..

```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 02
       serial: 00:1c:c0:db:15:84
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.178.101 latency=0 link=no multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:2000(size=256) memory:90100000-90100fff memory:90320000-9032ffff(prefetchable) memory:90300000-9031ffff(prefetchable)

```
```

ifconfig
eth1      Link encap:Ethernet  Hardware Adresse 00:1c:c0:db:15:84  
          inet Adresse:192.168.178.101  Bcast:192.168.178.255  Maske:255.255.255.0
          inet6-Adresse: fe80::21c:c0ff:fedb:1584/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:811 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Basisadresse:0xe000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:445 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:38650 (38.6 KB)  TX bytes:38650 (38.6 KB)

```

I´ll be gone for bout 12h, it´s getting late here. Thanks guys so far! :)

---

### Post by Peter09 on 2010-06-14
Well according to ifconfig you have an ethernet address of

> inet Adresse:192.168.178.101
so presumably your card is working

---

### Post by Iowan on 2010-06-14
Now the question is whether **route** uses eth1 or something else (eth3?).

---

### Post by Peter09 on 2010-06-15
Agreed Iowan,
so can we see the output of the command
 
```
route
```

---

### Post by kuckie on 2010-06-15
Ok here´s an update:

Booted up and now the device is ETH4 again...

One more thing, since this incident I can´t shutdown properly, machine hangs with the shutdown splash. This also never occured before.

the output:
```

ifconfig
eth4      Link encap:Ethernet  Hardware Adresse 00:1c:c0:db:ff:84  
          inet6-Adresse: fe80::21c:c0ff:fedb:ff84/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:90 (90.0 B)
          Interrupt:27 Basisadresse:0xc000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:3600 (3.6 KB)  TX bytes:3600 (3.6 KB)

lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth4
       version: 02
       serial: 00:1c:c0:db:ff:84
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:2000(size=256) memory:90100000-90100fff memory:90320000-9032ffff(prefetchable) memory:90300000-9031ffff(prefetchable)

route                                                                                                              
Kernel-IP-Routentabelle                                                                                                        
Ziel            Router          Genmask         Flags Metric Ref    Use Iface        

```

As you can see now there is no IP adress assigned, later I will try to get to the state it was before (with IP assigned) and then post the output of route again.

I just wanted to mention, this is my home and bussiness - backup machine w/ about 1TB of data on it, encrypted. Backing all up took about 1,5 days, so performing a new clean install just aint an option. :-s

---

### Post by Peter09 on 2010-06-15
What is the content of the file
 
/etc/iftab

---

### Post by Peter09 on 2010-06-15
This thread may cover it
 
[http://ubuntuforums.org/showthread.php?t=1366248](http://ubuntuforums.org/showthread.php?t=1366248)

---

### Post by kuckie on 2010-06-15
Here´s what I did: changed /etc/network/interfaces back to eth4 and static IP.

Now I got a (for me) normal looking route etc. but still no networking.

```

route
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.178.0   *               255.255.255.0   U     0      0        0 eth4
link-local      *               255.255.0.0     U     1000   0        0 eth4
default         192.168.178.1   0.0.0.0         UG    100    0        0 eth4

ifconfig
eth4      Link encap:Ethernet  Hardware Adresse 00:1c:c0:db:ff:84  
          inet Adresse:192.168.178.101  Bcast:192.168.178.255  Maske:255.255.255.0
          inet6-Adresse: fe80::21c:c0ff:fedb:ff84/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:138 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:174 (174.0 B)
          Interrupt:16 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:8285 (8.2 KB)  TX bytes:8285 (8.2 KB)
```

---

### Post by Peter09 on 2010-06-15
Deleted

---

### Post by Peter09 on 2010-06-15
Are you on eth3 or eth4, all your routing is using eth4.
you can delete these routes by
 
```
route delete <ip address>
```
 
The thing is - is your ethernet number (eth3) staying constant when you reboot. You may find just rebooting will reset your routing table.

---

### Post by kuckie on 2010-06-15
> **Peter09 said:**
> Are you on eth3 or eth4, all your routing is using eth4.
 
The thing is - is your ethernet number (eth3) staying constant when you reboot. You may find just rebooting will reset your routing table.

This turn the device  was on eth4. 

To your second question: occasionally. About the last 5 boots it stayed on eth4. 
It seems pretty random, it started with eth1 after installation about 8 weeks ago. (I remember wondering back then, why it´s not eth0). After the "network-crash" it was on eth3, then eth4, then eth0, then eth4, where it stayed the last 5 boots.. :confused:

---

### Post by Peter09 on 2010-06-15
can you provide the routing table output again.
 
Also can you ping your default gateway?

---

### Post by Peter09 on 2010-06-15
Did you read the thread that I sent?

---

### Post by kuckie on 2010-06-15
Yeah I read that before and looked into the 70-persistent-net.rules file.

But I havent been too keen yet on trying the proposed way described in the thread, as I absolutely don´t know what I would do there, I´m afraid if something goes wrong with that I wont be able to fix it. 

But if you say it´s ok and safe to try it out I will..

---

### Post by kuckie on 2010-06-15
> **Peter09 said:**
> can you provide the routing table output again.
 
Also can you ping your default gateway?

I´ll get back to you with that tonight.

---

### Post by kuckie on 2010-06-15
heyyy, now it´s on eth5. guess the fun never stops :popcorn:

```

route
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.178.0   *               255.255.255.0   U     0      0        0 eth5
link-local      *               255.255.0.0     U     1000   0        0 eth5
default         192.168.178.1   0.0.0.0         UG    100    0        0 eth5

route delete 192.168.178.0
SIOCDELRT: No such process
route delete link-local
SIOCDELRT: Invalid argument
route delete 192.168.178.1
SIOCDELRT: No such process
route delete default

route
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.178.0   *               255.255.255.0   U     0      0        0 eth5
link-local      *               255.255.0.0     U     1000   0        0 eth5

ifconfig
eth5      Link encap:Ethernet  Hardware Adresse 00:1c:ff:db:ff:84  
          inet Adresse:192.168.178.101  Bcast:192.168.178.255  Maske:255.255.255.0
          inet6-Adresse: fe80::21c:ffff:fedb:ff84/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:92 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:1414 (1.4 KB)
          Interrupt:16 Basisadresse:0xa000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:7478 (7.4 KB)  TX bytes:7478 (7.4 KB)

```

Cant ping my gateway, all packets dropped..

---

### Post by Peter09 on 2010-06-15
Before you edit the file save a copy

```
cp <filename> <filename_saved>
```

then if you make a mistake you can just copy back the old one.

---

### Post by kuckie on 2010-06-16
So I followed all the steps from the other thread. The device is now back on eth0, but except that, nothing changed.

1. Have to restart the network after reboot from console to get an IP assigned
2. Dont have no net, cant ping anything here, cant reach any website :???:

---

### Post by Peter09 on 2010-06-16
What does ifconfig and route show

---

### Post by kuckie on 2010-06-17
same as before..

```

route
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.178.0   *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.178.1   0.0.0.0         UG    100    0        0 eth0

ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:1c:c0:db:ff:84  
          inet Adresse:192.168.178.101  Bcast:192.168.178.255  Maske:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Basisadresse:0x8000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:4387 (4.3 KB)  TX bytes:4387 (4.3 KB)

```

Don´t know if it´s important, but the third line output of the route command needs at least 15 seconds to appear..

---

### Post by Peter09 on 2010-06-17
Not the same as before, note this line

> default         192.168.178.1   0.0.0.0         UG    100    0        0 eth0

this show your default gateway (UG) which is your router - this is good.

---

### Post by kuckie on 2010-06-17
> **Peter09 said:**
> Not the same as before, note this line
this show your default gateway (UG) which is your router - this is good.

Ok, so what to do next?

---

### Post by kuckie on 2010-06-18
I booted up from an usb-installation, which ran before flawless on the same machine. Guess what? No network.

I think the hardware is jammed. Too bad, it´s an Micro-ATX board & case, otherwise I would have lots of ethernet cards here to put in... ](*,)

I´m open to any more ideas what else to try, or on how to confirm, the hardware is jammend.

---

### Post by Peter09 on 2010-06-18
Don't think its that because you are getting an Ip address from your router and also the default gateway details.
 
Just as a sanity check
 
1. reboot your router
2. ```
ping google.com
``` - what do you get
3 use the command ```
traceroute google.co.uk
``` what do you get
4. if you have another machine on the network - try pinging between the two.
5. does your router see your machine as connected.

---

### Post by kuckie on 2010-06-19
I have to put this on hold right now. Thanks for your help!

---

