---
title: "problem with PCMCIA ethernet card"
date: 2006-02-18
forum: Networking &amp; Wireless
---

### Post by sanandana on 2006-02-18
hello,

I bought a second hand PCMCIA ethernet card 3Com 3CCFE575CT.
To connect to the internet, I use an ethernet Adsl modem/router SpeedTouch510, which gives DHCP service. The modem/router works perfectly on my MacMini running Ubuntu Breezy. For instance, when I plug the RJ45 wire in the MacMini, the LAN del lights.

:confused:  But, on my laptop, during the installation of Ubuntu Breezy, the network configuration aborted: the DHCP server (my modem/router) is not found, although the PCMCIA card is well recognized. I noticed that when I plug the ethernet wire in the PCMCIA card, the Lan del of the modem does *not* light.

PCMCIA service is well started by Ubuntu and the card seems to be properly installed.

How to diagnose this problem?

Regards,

Sanandana

---

### Post by bscbrit on 2006-02-18
If you start troubleshooting with this link you will be able to identify exactly where the problem lies.  Do that, and then return here.

[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

---

### Post by sanandana on 2006-02-18
So, here comes the first message:

sanandana@ubuntu:/$ sudo mii-tool eth0
eth0: no link


What does it mean? a configuration problem or a hardware one?

Thanks

---

### Post by bscbrit on 2006-02-18
OK, lets start with a look at your interfaces file

/etc/network/interfaces

But the message that you received suggests that the pcmcia card does not even have a driver installed.  What did you mean in your original post when you said "although the PCMCIA card is well recognized".  If you open System -> Administration -> Networking, does the eth0 card show there?

---

### Post by sanandana on 2006-02-18
oups,

I only installed Ubuntu in server because I would like to install xubuntu-desktop. So, no graphical tool. Which command should I use instead?

Here comes the /etc/network/interfaces:

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
               script grep
               map eth0

---

### Post by bscbrit on 2006-02-18
[http://www.ubuntuforums.org/showthread.php?t=87643](http://www.ubuntuforums.org/showthread.php?t=87643)

The computer is NOT configured for your PCMCIA card - I am still not sure what you meant by your original post when you said "although the PCMCIA card is well recognized".  It isn't.  Do you know which drivers you need for it?  No matter.

Start following the instruction contained in the link and come back when you get stuck.  I'll be waiting.  If you cannot get the computer to even recognise your PCMCIA card run the following at the command line and come back with the results:

lspci

---

### Post by bscbrit on 2006-02-18
How's it going?

---

### Post by sanandana on 2006-02-19
Good morning,

I launched all the commands you prescribed in the other thread. I am not able to diagnose anything, I have no network knowledge. I only know my modem/router IP: 10.0.0.138

Here comes the results:

```
sanandana@samasta:~$ ifconfig eth0
eth0      Lien encap:Ethernet  HWaddr 00:01:02:E7:1B:EE
          adr inet6: fe80::201:2ff:fee7:1bee/64 Scope:Lien
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interruption:10 Adresse de base:0x4000
```


```
sanandana@samasta:~$ lspci | grep Eth
0000:02:00.0 Ethernet controller: 3Com Corporation 3cCFE575CT CardBus [Cyclone] (rev 10)

sanandana@samasta:~$ lsmod | grep mii
mii                     5248  1 3c59x

sanandana@samasta:~$ sudo ifconfig eth0 up
sanandana@samasta:~$
```

--> no message here

```
sanandana@samasta:~$ ifconfig eth0
eth0      Lien encap:Ethernet  HWaddr 00:01:02:E7:1B:EE
          adr inet6: fe80::201:2ff:fee7:1bee/64 Scope:Lien
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interruption:10 Adresse de base:0x4000


sanandana@samasta:~$ route -n
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
sanandana@samasta:~$
```


```
sanandana@samasta:~$ ping 10.0.0.138
connect: Network is unreachable
```


```
sanandana@samasta:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:01:02:e7:1b:ee
Sending on   LPF/eth0/00:01:02:e7:1b:ee
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```


What is your opinion?


thanks,

Sanandana

---

### Post by bscbrit on 2006-02-19
Can you show me the contents of /etc/networking/interfaces please?  If it hasn't changed from the one you showed me in post #5 then just say so.

We will try to configure your network manually.

---

### Post by bscbrit on 2006-02-19
This should configure your ethernet card.  Put this in your 'interfaces' file - removing all of the existing data - and then 'sudo /etc/init.d/networking restart'.  I've got to leave the forum in about half an hour and will be back on later this afternoon.  But I'm sure that there will be others who will assist in the meantime.


> 
# The loopback network interface
auto lo eth0
iface lo inet loopback
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface eth0 inet static
address 10.0.0.2
netmask 255.0.0.0
gateway 10.0.0.138


---

### Post by sanandana on 2006-02-19
hello,

first, the content of /etc/network/interfaces:

```

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface eth0 inet dhcp

auto eth0
```


I performed the change you explained in /etc/network/interfaces and restart the network ; no change: impossible to ping the router.

---

### Post by bscbrit on 2006-02-19
OK, can you ping your card from the command line?

ping 10.0.0.2 -c 5

If not, then your card is not installed correctly, if yes, then it is only(?!) a network configuration problem.

---

### Post by sanandana on 2006-02-19
it pings!

```
sanandana@samasta:~$ ping 10.0.0.2 -c 5
PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.
64 bytes from 10.0.0.2: icmp_seq=1 ttl=64 time=0.084 ms
64 bytes from 10.0.0.2: icmp_seq=2 ttl=64 time=0.075 ms
64 bytes from 10.0.0.2: icmp_seq=3 ttl=64 time=0.070 ms
64 bytes from 10.0.0.2: icmp_seq=4 ttl=64 time=0.075 ms
64 bytes from 10.0.0.2: icmp_seq=5 ttl=64 time=0.055 ms

--- 10.0.0.2 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3998ms
rtt min/avg/max/mdev = 0.055/0.071/0.084/0.014 ms
```

what is the matter?

---

### Post by bscbrit on 2006-02-19
Your card is configured correctly but I suspect that you do not have the correct settings for your gateway and DNS server.

Confirm that you have the network cable securely linking the network card on your computer and your modem.  Please give me the make and model number of your modem / router or whatever.  It looks like its address is NOT 10.0.0.138 - which really doesn't sound like the type of catchy, easily remembered IP address that manufacturers like anyway. 

What DNS addresses has your ISP given you to use?  if you do not know, what is the name of your ISP and please give me a web link to them.

---

### Post by sanandana on 2006-02-19
I can confirm that the network cable is well plugged.

My provider is wanadoo.  [www.wanadoo.fr](www.wanadoo.fr)

Actually, I am writing this post on a MacMini running Ubuntu Breezy, connected to a Thomson SpeedTouch 510 ADSL modem/router. So, it works. Here comes informations about the router, supplied by the web interface I get when I connect to the modem through Firefox [http://10.0.0.138](http://10.0.0.138).


```
Interface : PPPoE_1
IP Addresses/Netmasks : 81.53.11.205/32
Primary DNS : 80.10.246.130
Secondary DNS : 80.10.246.3

```

```
Service Name : Routed PPPoE - DHCP - NAPT
Service Description : Routed PPPoE Packet Service configuration using always-on session connectivity.
```

```
IP Address Table
PPPoE_1 : 81.53.11.205/32  Auto  napt
eth0 : 169.254.141.11/16  Auto  none
eth0 : 10.0.0.138/24 User none
loop : 127.0.0.1/8  Auto  none
```

---

### Post by bscbrit on 2006-02-19
OK - I'm puzzled....

Can you ping your router using 10.0.0.138 from the MacMini?

What are the contents of /etc/network/interfaces and /etc/resolv.conf on the MacMini?

How is the MacMini connected to the router - ethernet?

---

### Post by sanandana on 2006-02-19
all the previous informations come from joining the router from the macmini, with Firefox, on IP 10.0.0.138

The MacMini is connected to the router with a RJ45 cable.

```
sanandana@MacMini:~$ ping 10.0.0.138
PING 10.0.0.138 (10.0.0.138) 56(84) bytes of data.
64 bytes from 10.0.0.138: icmp_seq=1 ttl=64 time=0.500 ms
64 bytes from 10.0.0.138: icmp_seq=2 ttl=64 time=0.376 ms
64 bytes from 10.0.0.138: icmp_seq=3 ttl=64 time=0.368 ms
64 bytes from 10.0.0.138: icmp_seq=4 ttl=64 time=0.372 ms
64 bytes from 10.0.0.138: icmp_seq=5 ttl=64 time=0.367 ms
64 bytes from 10.0.0.138: icmp_seq=6 ttl=64 time=0.370 ms
64 bytes from 10.0.0.138: icmp_seq=7 ttl=64 time=0.584 ms
64 bytes from 10.0.0.138: icmp_seq=8 ttl=64 time=0.378 ms

--- 10.0.0.138 ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 7000ms
rtt min/avg/max/mdev = 0.367/0.414/0.584/0.078 ms
sanandana@MacMini:~$
```


here comes, from the MacMini, /etc/network/interfaces :
```

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
```

and /etc/resolv.conf :
```

search lan
nameserver 10.0.0.138
```

---

### Post by bscbrit on 2006-02-20
In that case, try switching the cable from the MacMini temporarily to your other computer.  With the settings being the same, there is no reason that I can think of that it shouldn't work.

---

### Post by sanandana on 2006-02-20
unfortunately, from the beginning, I use the same cable...

So, do you agree it looks like an hardware problem?

I wrote before that it is a second hand PCMCIA card.

---

### Post by bscbrit on 2006-02-20
Yes, it looks very much like your NIC is not working.  We have discounted everything else.

---

### Post by sanandana on 2006-02-20
thank you very much for your help.

I will buy another card [-o<

---

### Post by sanandana on 2006-02-28
I bought a new PCMCIA ethernet card: it works perfectly...

---

