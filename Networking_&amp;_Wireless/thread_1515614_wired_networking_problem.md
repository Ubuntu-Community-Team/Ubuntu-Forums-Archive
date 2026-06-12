---
title: "wired networking problem"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by robsarm on 2010-06-22
just installed 10.04 on my wifes computer. I knew I was going to have to do some work to get her wireless adapter to work but I (incorrectly) assumed that the wired connection would work so I didn't test it on the live cd before installing. Now I am stuck with no internet connection on her machine.
I've read some posts of similar problems and here is some more information.

sudo lshw -class network

*- network
description: Ethernet interface
product: 82562ez 10/100 Ethernet Controller
vendor: Intel Corporation 
physical id: 8
bus info: pci@0000:01:08.0
logical name: eth0
version: 02
serial: 00:13:20:2d:f9:56
size: 10mb/s
capacity: 100mb/s
width: 32 bits
clock: 33mhz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-f
d 100 bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=n/a latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=mii speed=10mb/s 
resources: irq:20 memory:feaff000-feafffff io port:ddc0(size=64)


ifconfig 

eth0     Link encap:Ethernet HWaddr 00:13:20:2d:f9:56
UP broadcast multicast MTU:1500 Metric:1
RX packets:0 Errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

LO      LINK Encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:72 errors:0 dropped:0 overruns:0 frames:0
TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 TXqueuelen:0
RX bytes:5600 (5.6 kb)  TX bytes: 5600 (5.6 kb)

hopefully I copied all of that correctly, my wife is reading off her computer to me across the room.
Any help greatly appreciated

---

### Post by dozdozez on 2010-06-22
edit the /etc/network/interfaces file. There your eth0 should be some lines like:

auto eth0
iface eth0 inet dhcp

if you configure the net through dhcp or:

auto eth0
iface eth0 inet static
address 192.168.1.41
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

if you configure it with a static ip
 
If in that file everything looks normal, try the command:
sudo  /etc/init.d/networking restart
The output of this command may be helpfull

---

### Post by robsarm on 2010-06-22
Thanks for the response

I edited the file
saved that, rebooted and now the networking icon on the desktop panel is gone
so I tried the networking restart

I got this:( I am omitting the copyright stuff)

*reconfiguring network interfaces....
There is already a pid file /var/run/dhclient.eth).pid with pid 1070
killed old client process, removed pid file
Internet Systems Consortium DHCP Client v3.1.3
(omitted copyright stuff)
Listenening on LPF/eth0/00:13:20:2d:f9:56
Sending on  LPF/eth0/00:13:20:2d:f9:56
Sending on  Socket/fallback
grep: /etc/resolv.conf: No Such file or directory

(more copyright stuff)

Listening on lpf/eth0/00:13:20:2d:f9:56
Sending on  lpf/eth0/00:13:20:2d:f9:56
sending on socket/fallback
DHCPDiscover on eth0 to 255.255.255.255 port 67 interval 4
"                                                      " 10
"                                                      " 13
"                                                      " 19
"                                                      " 12
"                                                      " 3
No dhcpoffers recieved.
No working leases in persistant database - sleeping.
grep: /etc/resolv.conf: No such file or directory

---

### Post by dozdozez on 2010-06-22
Ummm....

is your net like 192.168.1... and has your router the ip 192.168.1.1?

if so try this: (as root or using sudo)

ifconfig eth0 inet 192.168.1.44            (44 or other number you like)
ping 192.168.1.1


1 if you get a reply from the router:
     dhclient eth0   -----> this ask for a dhcp connection, if you ca connect this way, you shold check the config files of the network

1 if you don't get a reply from the router
  emmm... dunno, check the cable connection...

---

### Post by Iowan on 2010-06-22
Some threads suggest that you must completely remove Network Manager for */etc/network/interfaces* to work properly - although I can't verify that. The "interfaces" entries are (probably) why NM (the networking icon) no longer acknowledges the interface. [This]("http://ubuntuforums.org/showthread.php?t=1156441") hasn't been as useful after Jaunty, but you're welcome to try some of the hints...

---

### Post by robsarm on 2010-06-22
no luck
my cable is good, checked it first
anybody??? Help?

---

