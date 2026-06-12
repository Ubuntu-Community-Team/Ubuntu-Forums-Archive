---
title: "Broadcast IP"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by DeWayne24 on 2009-11-15
I have two problems, I want to fix the one first. I am trying to get a static IP changed on my 9.04. I am showing a connection on the System>Administration>Network for both the wired and wireless. The first problem I need to deal with is the wired connection. When I have it set to DHCP it will connect to the Internet. When I change it to the static IP it will not. When I run the ifconfig I get the information below:

dewayne@APTserver:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:18:4a:7c:9b  
          inet addr:70.58.122.41  Bcast:**[COLOR=Red]70.58.122.[/COLOR][COLOR=Red]255[/COLOR]**  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:fe4a:7c9b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66144 (66.1 KB)  TX bytes:16413 (16.4 KB)
          Interrupt:252 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:81 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20905 (20.9 KB)  TX bytes:20905 (20.9 KB)

virbr0    Link encap:Ethernet  HWaddr 56:32:5c:c4:0c:75  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::5432:5cff:fec4:c75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:6868 (6.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:d0:83:d9  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Memory:dbfe0000-dbff0000 

The problem is that the broadcast IP needs to be 70.58.122.47. 

 I have changed the /ETC/Network/interfaces file to read:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface wlan0 inet dhcp
address 70.58.122.41
netmask 255.255.255.0
gateway 70.58.122.46
wireless-key 2424242424
wireless-essid ACTIONTEC

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet static
        address 70.58.122.41
        netmask 255.255.255.0
        network 70.58.122.40
        broadcast **[COLOR=Red]70.58.122.47[/COLOR]**
        gateway 70.58.122.46

after I reboot I still get the broadcast IP as the wrong one. 

Any ideas on how to correct this?

---

### Post by Iowan on 2009-11-16
Try a subnet mask of 255.255.255.248
I used [this]("http://www.tech-faq.com/calculate-broadcast-address.shtml") calculator with your address 70.58.122.41 and a subnet mask of 255.255.255.248 and got broadcast address 70.58.122.47 with network address 70.58.122.40.

---

### Post by DeWayne24 on 2009-11-17
No luck, what I have found out is this. Wicd does not show the wireless connection, but from the system>network it does show the wireless. Also when using Wifi-Radar it is picking up signals. Could this pick up signals if the card is not being recognized.

---

### Post by DGortze380 on 2009-11-18
This is an internet routeable address.
Your ISP is clearly giving you a DHCP address, if you want a static address, you'll need to pay for one from your ISP. Or use a service like dyndns.

---

### Post by DeWayne24 on 2009-11-18
that is exactly right I am paying for 5 of them. I have a block of 8, five are usable.

---

### Post by DGortze380 on 2009-11-18
> **Iowan said:**
> Try a subnet mask of 255.255.255.248
I used [this]("http://www.tech-faq.com/calculate-broadcast-address.shtml") calculator with your address 70.58.122.41 and a subnet mask of 255.255.255.248 and got broadcast address 70.58.122.47 with network address 70.58.122.40.

This is your problem then. 
You're using the wrong netmask. Verify with your ISP that your netmask is 255.255.255.248 and edit interfaces accordingly.


You've specified 255.255.255.0 which would put the network address at .0 and broadcast at .255 regardless of your static entry.

---

### Post by dc0m on 2009-11-19
Guys, he is trying to setup local ip address. So his setup was initially correct. I am guessing it might be problem with nameserver. His LAN has notihing to do with ISP and public ip address.

---

