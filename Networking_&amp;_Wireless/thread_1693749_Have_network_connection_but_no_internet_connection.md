---
title: "Have network connection but no internet connection."
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by mjaywoods on 2011-02-23
Hi,

I need help.

I switched the IP on my Ubuntu Lucid box to a static IP and have now lost internet connection.

this is my interface settings

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.9.200.196
netmask 255.255.255.0
network 192.9.200.0
broadcast 192.9.200.255
gateway 192.9.200.250

Any ideas?

---

### Post by Savio2010 on 2011-02-23
Are you directly connected to the internet ?
  
  The IP address that you have put is a public address.
 
 I guess the ip must be 192.168.200.x if you are behind a router.
 
 switch back to dhcp and then run the following command at terminal

ifconfig

note down the ip address, gateway, subnetmask and apply the same as static.....

you should now get connectivity.

if your subnetmask is 255.255.255.0 the ip add can be any thing in the last octet 192.168.200.x, just replace the x.

---

### Post by mjaywoods on 2011-02-23
Just tried what you said, and reverted to dhcp...

Having trouble getting back on the internet.

ifconfig shows the following


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:62002 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62002 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5600561 (5.6 MB)  TX bytes:5600561 (5.6 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:8c:04:17:2c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Noticed when I'm on the static IP I can ping the gateway, but can not ping an external IP not sure if that helps.

ifconfig with static IP is...


eth0      Link encap:Ethernet  HWaddr 00:1d:09:77:35:46  
          inet addr:192.9.200.196  Bcast:192.9.200.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe77:3546/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77962700 errors:4 dropped:0 overruns:0 frame:2
          TX packets:55244107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:882710098 (882.7 MB)  TX bytes:4069619051 (4.0 GB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:62010 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62010 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5601219 (5.6 MB)  TX bytes:5601219 (5.6 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:8c:04:17:2c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Savio2010 on 2011-02-24
Are you behind a router.... yes or no or you directly connected to the net. If you are behind a router then the ip configuration

eth0 Link encap:Ethernet HWaddr 00:1d:09:77:35:46
inet addr:**192.9.200.196** Bcast:192.9.200.255 Mask:255.255.255.0
inet6 addr: fe80::21d:9ff:fe77:3546/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:77962700 errors:4 dropped:0 overruns:0 frame:2
TX packets:55244107 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:100
RX bytes:882710098 (882.7 MB) TX bytes:4069619051 (4.0 GB)
Memory:fdfc0000-fdfe0000

must be incorrect. This is a public ip (mean you have put a external ip address directly on your PC). Pings should work to 192.9.200.196 if you can ping your gateway.

If you are connected to the router and the router to the net then you should be using a private ip address like 192.168.x.x range.

If you are directly connected to the net then your isp must be providing you with a dhcp address, find out........ you cannot use static ip address unless you perchase one.

Lets assume you have correctly configured the interface.......... what about DNS? have you configured it.
DNS --  Domain Name Server : Helps you resolve host names into ip addreses.

---

