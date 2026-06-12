---
title: "Problems with the Wired Connection"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by braghetto on 2009-04-27
One week ago I was still using Ubuntu 8.10 but for no reason one day the wired connection wasn't working at all.. instead of looking for solutions, I thought to take this opportunity and start from zero installing the 9.04, however, the problem of wired connection is not resolved. I am sure that the problem is in the notebook because if I link another pc (windows) with the same cable I connect without problems. This is the result of the command ifconfig:

>            diego@diego-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:e9:78:56  
          inet addr:10.248.27.1  Bcast:10.248.27.3  Mask:255.255.255.252
          inet6 addr: fe80::216:36ff:fee9:7856/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:195 errors:0 dropped:0 overruns:0 frame:0
          TX packets:149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15102 (15.1 KB)  TX bytes:22886 (22.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10848 (10.8 KB)  TX bytes:10848 (10.8 KB)

pan0      Link encap:Ethernet  HWaddr 1e:b9:22:92:b7:6e  
          inet6 addr: fe80::1cb9:22ff:fe92:b76e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:11271 (11.2 KB)

pan0:avahi Link encap:Ethernet  HWaddr 1e:b9:22:92:b7:6e  
          inet addr:169.254.7.182  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:50:0d:bd  
          inet6 addr: fe80::219:d2ff:fe50:dbd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2361 (2.3 KB)  TX bytes:2030 (2.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-50-0D-BD-64-62-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 

 I've also tryed to ping ubuntu.com from the network tool but the result was "The address ubuntu.com cannot be found". The cable is correctly connected and recognised from the network manager applet.

How can I fix this problem? I looked in forums for hours before posting this thread..

Thanx in advance!

---

### Post by chili555 on 2009-04-27
> diego@diego-laptop:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:16:36:e9:78:56
inet [COLOR="Red"]addr:10.248.27.1 [/COLOR]Bcast:10.248.27.3 Mask:255.255.255.252
inet6 addr: fe80::216:36ff:fee9:7856/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:195 errors:0 dropped:0 overruns:0 frame:0
TX packets:149 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
[COLOR="Red"]RX bytes:15102 (15.1 KB) TX bytes:22886 (22.8 KB)[/COLOR]You sure look connected to me! You have an IP address and seem to be sending and receiving packets. What symptom do you have that tells you that you may not be connected? Did you get the IP address statically or with DHCP? What is the result of this command?```
ping -c3 74.125.67.103
```

---

### Post by Iowan on 2009-04-27
How are you connected - router, modem, direct? Static or DHCP adddress? Can the machine **ping** it's gateway (router, modem, etc)?

---

### Post by braghetto on 2009-04-27
ping -c3 74.125.67.103

PING 74.125.67.103 (74.125.67.103) 56(84) bytes of data.
--- 74.125.67.103 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms 
I''m connected directly with DHCP adddress..

---

### Post by chili555 on 2009-04-27
> I''m connected directlyTo what? A router or a DSL modem or...? Perhaps the modem or connection from your house to the Internet Service Provider does not have an IP address. When you do:```
route -n
```Find the address of the gateway. Can you ping the gateway? Also, please post:```
cat /etc/resolv.conf
```

---

### Post by braghetto on 2009-04-27
>  	 	 diego@diego-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.248.27.0     0.0.0.0         255.255.255.252 U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 pan0
0.0.0.0         10.248.27.2     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 pan0
diego@diego-laptop:~$ cat /etc/resolv.conf 
# Generated by NetworkManager
domain qmul.ac.uk
search qmul.ac.uk


I can't understand what's wrong

---

### Post by chili555 on 2009-04-27
> I can't understand what's wrong The more I see, the less I understand here, too! Please open a terminal and do:```
sudo dhclient eth0
```Let's see if we get a new, working IP address or, worse case, some clues as to what's going wrong. Also, what does this tell us?```
ping -c3 10.248.27.2
```

---

### Post by haineb on 2009-04-27
Are you hardcoding an IP address via /etc/network/interfaces ?
I've run into what seems to be the same mysterious problem when I attempt to hardcode.
([http://ubuntuforums.org/showthread.php?t=1137896](http://ubuntuforums.org/showthread.php?t=1137896))

Edit:
Nevermind, I see you're using DHCP. Have you made any customizations to that file?

---

### Post by braghetto on 2009-04-27
>  	 	 diego@diego-laptop:~$ sudo dhclient eth0
[sudo] password for diego: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:16:36:e9:78:56
Sending on   LPF/eth0/00:16:36:e9:78:56
Sending on   Socket/fallback
DHCPREQUEST of 10.248.27.1 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.248.27.1 from 138.37.248.254
bound to 10.248.27.1 -- renewal in 836 seconds.
diego@diego-laptop:~$ ping -c3 10.248.27.2
PING 10.248.27.2 (10.248.27.2) 56(84) bytes of data.

--- 10.248.27.2 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms


I didn't edit the /etc/network/interfaces, the content of that file is the following:

auto lo
iface lo inet loopback

I'm getting crazy ](*,)](*,)

---

### Post by braghetto on 2009-04-28
i have to change something in /etc/network/interfaces ?

---

### Post by ktechman on 2009-04-28
Do you have the wired and wireless connected at the same time try to turn off the wireless switch on the front of the laptop.

---

### Post by braghetto on 2009-04-28
already done... nothing changed!!! ](*,)](*,)](*,)

---

### Post by chili555 on 2009-04-28
> DHCPACK of 10.248.27.1 from 138.37.248.254This is very weird! You would expect the DHCP server, if it was on a gateway, router or other access point, to give an IP address in the range of 138.17.248.x. I wonder why it's handing you 10.248.27.1. I've never seen this before.

When you attach the Windows computer and run:```
ipconfig /all
```Do the settings and addresses look the same? May we please know the answer to this question?>  [QUOTE]I''m connected directlyTo what? A router or a DSL modem or...?[/QUOTE]

---

### Post by braghetto on 2009-04-29
> Atheros L2 Fast Ethernet 10/100 Base-T Controller
    Connection Name: Connessione alla rete locale (LAN)
    GUID: {F808D60C-4FD2-478F-AD5F-C97FCFF4DC23}
    Index: 0x10003
    Media Type: Ethernet
    MAC: 00-1F-C6-1E-12-C6
    IP Address: 10.248.10.1
    Subnet Mask: 255.255.255.252
    APIPA: enabled
    Gateway: 10.248.10.2
    DHCP
        DHCP Server: 138.37.248.254
        Lease Obtained: 29.04.09 10:20
        Lease Expires: 29.04.09 10:50
    DNS
        DNS Suffix: qmul.ac.uk
        DNS Server: 138.37.6.1
        DNS Server: 138.37.7.1

Destination Address Destination Mask    Next Hop            IF Index  Metric    Persistent
0.0.0.0             0.0.0.0             10.248.10.2         0x10003   30        
10.248.10.0         255.255.255.252     10.248.10.1         0x10003   30        
10.255.255.255      255.255.255.255     10.248.10.1         0x10003   30        
224.0.0.0           240.0.0.0           10.248.10.1         0x10003   30        
255.255.255.255     255.255.255.255     10.248.10.1         0x10003   1       

I had a similar problem 1 year ago with ubuntu 8.04 but with the wireless connection and I fixed it doing this instructions:

	 	 1) adding this line to /etc/dhcp3/dhclient.conf :
*prepend domain-name-servers  208.67.222.222, 208.67.220.220;*

2) adding this two lines in  /etc/network/interfaces 
[I]auto eth1
iface eth1 inet dhcp[/I]

3) executing this command: (G604T_WIRELESS is the ssid of my home wireless)
sudo iwconfig eth1 essid G604T_WIRELESS mode managed key  ap 00:11:95:9D:42:44

4) finally executing this command
sudo /sbin/dhclient eth1 

Then I had no problem upgrading to 8.10 cause I just upgraded so i thinks the dhclient file was conserved. I just wrote this to give you more informations.

I live inside the campus of the university, everybody is connected with the lan cable i think to a router...

](*,)

---

### Post by braghetto on 2009-04-29
Now that i'm connected with the wireless connection, ifconfig shows this:

> 
wlan0     Link encap:Ethernet  HWaddr 00:19:d2:50:0d:bd  
          inet indirizzo:10.225.211.1  Bcast:10.225.211.3  Maschera:255.255.255.252
          indirizzo inet6: fe80::219:d2ff:fe50:dbd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57812 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20465 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:52573395 (52.5 MB)  Byte TX:2180326 (2.1 MB)


with IP 10.225.211.1 .. so it's not totally weird the result of ifconfig eth0..

---

