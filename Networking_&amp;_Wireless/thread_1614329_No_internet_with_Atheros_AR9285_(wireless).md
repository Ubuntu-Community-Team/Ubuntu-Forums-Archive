---
title: "No internet with Atheros AR9285 (wireless)"
date: 2010-11-05
forum: Networking &amp; Wireless
---

### Post by perlon on 2010-11-05
Hi, I've a big trouble that curses me for months.
I've an Asus K52Jc laptop with wireless card Atheros AR9285, Ubuntu 10.10 and this network set-up:
a WDSL (so an antenna on my house) wired to a switch; the switch shares connection through 2 ethernets cables: one to my uncle house, one to my router Netgear DG834v5.
If I connect my laptop via ethernet, internet works good, if I connect to my router, wireless works (I can ping my router), but no internet. I've been helped a lot in official ubuntu chat: after some tries we understood that the problem aren't drivers, isn't Netgear, but probably it's something messed up in routes or arp cache.
Anyway note that I have also some difficulties to ping my router, on 3 tries he often loses 1 or 2 packets.

[B]
Recap[/B]:
*Ubuntu 10.10 x64
*a WDSL antenna (maybe with IP 192.168.0.1, I can't access its settings)
*router Netgear (IP 192.168.0.1, DHCP disabled, 802.11b&g)
*my laptop (IP 192.168.0.50)

```
[B]
[sudo lshw -C Network[/B]]
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 1c:4b:d6:a8:a7:0d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-generic firmware=N/A ip=192.168.0.50 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d4c00000-d4c0ffff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:04:00.5
       logical name: eth0
       version: 03
       serial: 48:5b:39:53:7e:21
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.6 duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:47 memory:d3800000-d3803fff ioport:a100(size=128) ioport:a000(size=256)


**[route -n]** (I add the loopback entry manually)
Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
127.0.0.0       0.0.0.0         255.0.0.0       U     0      0        0 lo     <--- added
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0


**[arp]**
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.0.1                      (incomplete)                              wlan0


**[ifconfig**]
eth0      Link encap:Ethernet  HWaddr 48:5b:39:53:7e:21  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)
          Interrupt:47 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:2864 (2.8 KB)  Byte TX:2864 (2.8 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:4b:d6:a8:a7:0d  
          indirizzo inet:192.168.0.50  Bcast:192.168.0.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::1e4b:d6ff:fea8:a70d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1029 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:98501 (98.5 KB)  Byte TX:14877 (14.8 KB)

[B]
[iwconfig][/B]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"CASA"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:22:3F:6C:99:4A   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```The one who will solve my problem will be rewarded with a giant bronze statue. (2000$ shipping cost :))

---

### Post by uncaspi on 2010-11-05
What browser do u use? Have you tried another one?

---

### Post by perlon on 2010-11-06
> **uncaspi said:**
> What browser do u use? Have you tried another one?

I only use Firefox, but that's not the point.
I can't ping google, I can't update software, etc... so internet doesn't work.

---

### Post by uncaspi on 2010-11-06
Can you ping your router?

---

### Post by uncaspi on 2010-11-06
Seems to be something with the nameservers. Look in /etc/resolv.conf and see if you have the nameservers listed.

---

### Post by depeha on 2010-11-06
same problem here.
here's my resolv.conf:
```
# Generated by NetworkManager
nameserver 192.168.1.254

```

I've also tried [_[COLOR="Blue"]this[/COLOR]_](http://ubuntuforums.org/showpost.php?p=9985581&postcount=1) without any luck :(

---

### Post by uncaspi on 2010-11-06
This point to the router. Then you have to log in to the router and see if the router have the nameserver to the ISP.

---

### Post by depeha on 2010-11-06
I cannot log in to router, because my ISP set up his own pass. (but I don't think there's problem in router... other computers, or my with windows can connect to internet)

Weird thing is, that I can connect to internet sometimes. (in LiveCD mode, right after installing system, or now... randomly)

---

### Post by uncaspi on 2010-11-06
Still I think it`s a router problem. In 3 years I trid 5 diffrent routers before I found a Linksys 3Com router that  was stable.
But maybe there is a way around the problem. First try to disable ipv6 in firefox. I think you type about:conf or something like that in the address field. Scroll down to ipv6 and disable it.

---

### Post by perlon on 2010-11-07
> **uncaspi said:**
> Can you ping your router?
Yes, I can.
And my resolv.conf is fine, I try several DNS, they're not the problem.

> This point to the router. Then you have to log in to the router and see if the router have the nameserver to the ISP.What do you mean? Should I set in the router my ISP DNS?
In Windows 7 wireless works good, without setting it.

Also, my router now is set on 802.11 b&g connection. Would be a good try to set 802.11 g only? ( my laptop supports b, g, n)

---

### Post by uncaspi on 2010-11-07
Yes you should set your ISP DNS in the router. I don`t think it has to do with the comm protocol so no matter g or b in 802.

---

### Post by uncaspi on 2010-11-07
To ensure that it has nothing to do with the network-manager you could try a manual connection.
Do the following. I assume your wifi card is named eth1 and not encrypted.
If not apply the key in iwconfig command line

sudo service network-manager stop

sudo /sbin/ifconfig eth1 up

sudo /sbin/iwlist scan

Find your router name and channel.
Mine is mjauritz channel 6

sudo /sbin/iwconfig eth1 essid "mjauritz" channel 6

sudo /sbin/dhclient eth1


See if this works.

---

### Post by perlon on 2010-11-08
Manual connection doesn't work.
Here's my output:

```
alberto@alberto-K52Jc:~$ sudo service network-manager stop
[sudo] password for alberto: 
network-manager stop/waiting
alberto@alberto-K52Jc:~$ sudo /sbin/ifconfig wlan0 up
alberto@alberto-K52Jc:~$ sudo /sbin/iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:22:3F:6C:99:4A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"CASA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000010c1a6d6f40
                    Extra: Last beacon: 720ms ago
                    IE: Unknown: 000443415341
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 070A474200010D14010D1400
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD890050F204104A00011010440001021041000100103B000103104700109C3F3A4F27669F8A3409288D2CF9D21B102100074E4554474541521023000844473833344776351024000844473833344776351042000A313233343536373839301054000800060050F20400011011001644473833344776352028576972656C65737320415029100800020086

alberto@alberto-K52Jc:~$ sudo /sbin/iwconfig wlan0 essid "CASA" channel 6
alberto@alberto-K52Jc:~$ sudo /sbin/dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/1c:4b:d6:a8:a7:0d
Sending on   LPF/wlan0/1c:4b:d6:a8:a7:0d
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

---

### Post by uncaspi on 2010-11-08
The scan found your router fine so probably the router is ok. Have you search the threads for AR9285. I did and find many with similar problems as you. Maybe you should get a new driver.

---

### Post by perlon on 2010-11-08
> **uncaspi said:**
> The scan found your router fine so probably the router is ok. Have you search the threads for AR9285. I did and find many with similar problems as you. Maybe you should get a new driver.

Yes I've read several of them for months; _theorically_ ath9k drivers are the one fitted for my Atheros. In some threads they say to use compat-wireless drivers, I've already tried it but indeed it contains ath9k drivers. In other threads they said madwifi drivers, but If I remember they're out-of-date.
I'm looking for other solutions everyday.

---

### Post by uncaspi on 2010-11-08
I`m not sure, but I`ll never seen all the Extra listing using iwlist scan. I don`t know if this point to something in the router.
Have you tried to upgrade the router firmware?

---

### Post by perlon on 2010-11-09
They already suggested me to update my router,but I'd like to leave this as the very last chance. It's a router that uses all my family, so I can't risk a delicate procedure like a firmware update, that sometimes bricks the device.
Let's first try other workarounds.

---

### Post by perlon on 2010-11-10
So, I edited two things:
-I set my ISP DNS in my router
-I enabled DHCP

The laptop still connects to internet totally random: first reboot after modifications it connected immediately! Second reboot it connected after about 20 minutes... and when it connects, internet works smoothly without any problem, so his difficulty is only at the first connecting instant.
I really don't understand what's going on. :confused:

---

### Post by uncaspi on 2010-11-10
Many here in the forum has problems with wireless in 10.10.Have you considered to downgrade to 10.04 which have less problems. I thought you only had problems with internet since you could ping the router, and now you said it takes 20 min to connect second time.

---

### Post by perlon on 2010-11-10
> **uncaspi said:**
> I thought you only had problems with internet since you could ping the router, and now you said it takes 20 min to connect second time.
Oh, I mean access the internet. I can always connect to router without problems.
Anyway, I had ubuntu 10.04 previously and had the exact same issues.

---

### Post by uncaspi on 2010-11-10
I read that someone got DNS from the router that didn`t work. Can you ping google.com

You could try to disable ipv6 in firefox by typing about:config in address field in the browser. Then scroll down to network.disable.ipv6
and set it to true

---

### Post by perlon on 2010-11-10
I already disabled ipv6.
I can ping google only when internet decides to work, obviously.

---

### Post by perlon on 2010-12-19
Solved!!
The problem was my strange home internet configuration..
Bye bye Windows! :D

---

### Post by kinogen on 2011-01-10
Can you tell me clearly your solution and your Internet configuration? I have exact the same problem as you and now it drives me crazy. I had to disable then enable my wifi several times to have Internet although the OS still finds my wifi card. Sometimes, this didn't work. My wifi card is AR9285 too.

---

### Post by jepong on 2011-01-12
installing linux-backports-modules-wireless-maverick-generic does wonders for me.

---

### Post by mr_black on 2011-04-14
Hello there! I have the same problem with the AR9285 on meerkat. I've been googling myself googly eyed and I can't find any fix. The compat-wireless does not help me.

---

