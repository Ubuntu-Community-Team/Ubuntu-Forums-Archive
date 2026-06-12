---
title: "No ethernet nor wireless with 11.04"
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by gen.svrd on 2011-07-13
Hi!
i'm a beginner with ubuntu and i installed 11.04 yesterday (so not yet familiar with the new desktop configuration). Also, I have the french version so i'll do my best to translate the terms in english...

I have a major problem: i can't connect to internet by ethernet cable or by wireless. The network icon is always empty. It doesn't detect the ethernet cable and the wireless networks around. I've tried different things i found on forums. I'v reinstalled the b43 package and rebooted. At the beginning i was only having problem with the wireless; i could connect via ethernet. But on one forum, a dude suggested the command 
```
unity --replace
compiz --replace
```
and it made my computer bug i had to force shutdown. When i restarted, ethernet cable was no longer detected.......

My PCI card is a Broadcom BCM4311. 

Here is what i get when i type some commands in terminal (notice the (...) means there is other stuff written but since i'm on another computer i can't copy-paste it so i just wrote the big lines):

**iwconfig:**

```

lo          no wireless extensions.

```

**sudo lshw -C network:**

```

*-network UNCLAIMED
description: Network controller
(...)

*-network UNCLAIMED
description: Ethernet controller
(...)

```
 

**lspci|grep -i ether:**

```

03:00.0 Ethernet controller`Broadcom Corporation BCM4311-B0 100Base-TX (rev 02)

```

**nm-tool:**

```

NetworkManager Tool

State: disconnected


```

**sudo iwlist scan:**

```

lo       Interface doesn't support scanning.


```


**ifconfig:**

```

lo      Link encap: Boucle locale
         inet adr:127.0.0.1 Masque...
         (...)
         Octets recus: 960 (960.0 B) Octets transmis:960 (960.0 B)


```

**rfkill list all:**

```
0: dell-wifi: Wireless LAN
Soft block: no
Hard block: no
```



hope i can get some ,help it's driving me crazy :(

---

### Post by ~!geek!~ on 2011-07-13
Just for a check could you please create a new user and see if the cable internet has started working again. If it does I would suggest you to keep with this user and delete the old user, but please do add new user to all groups original user belonged to. (I m suggesting u to keep new user and remove only because you recently installed ubuntu, so its a good idea to have a new user if internet works with it). 
I am reminding you again not to delete old user before adding new user to all the groups old user belonged to. Google it to learn how to add new user to a pre-existing group and all. This compiz and unity thing together is a pain, man. Seriously.

---

### Post by gen.svrd on 2011-07-14
thanks a lot for the reply!!! unfortunaltely, it didn't work..

i decided to reinstall 11.04. Now ethernet is back, but wireless is still a problem. i've checked other threads, but seems like nobody got the same message than me when i type 

**sudo lshw -C network**:

```
genevieve@genevieve-Vostro-1500:~$ sudo lshw -C network
[sudo] password for genevieve: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:86:fb:10
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.103 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:fe5fe000-fe5fffff
```
[B]
iwconfig:[/B]

```
genevieve@genevieve-Vostro-1500:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```
[B]
ifconfig:[/B]

```
eth0      Link encap:Ethernet  HWaddr 00:1c:23:86:fb:10  
          inet adr:192.168.1.103  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::21c:23ff:fe86:fb10/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:1688 erreurs:0 :0 overruns:0 frame:0
          TX packets:1380 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:1898485 (1.8 MB) Octets transmis:301817 (301.8 KB)
          Interruption:17 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:12 erreurs:0 :0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:720 (720.0 B) Octets transmis:720 (720.0 B)

```

i've tried to install these packages (suggested by another thread) :

broadcom-sta-common
firmware-b43-installer
b43-fwcutter

but it made my ethernet connection disappear. i completely suppressed the packages and ethernet is back again...

---

### Post by gen.svrd on 2011-07-14
Problem solved!!!

i found the solution there: 

[http://askubuntu.com/questions/38327/broadcom-bcm4311-wireless-not-working](http://askubuntu.com/questions/38327/broadcom-bcm4311-wireless-not-working)

:D

---

