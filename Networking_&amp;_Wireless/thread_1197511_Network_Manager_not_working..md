---
title: "Network Manager not working."
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by heviejob on 2009-06-26
[B]Hi.
[/B]
I recently Installed wicd to manage my network connections which removed the network manager. Later I reinstalled the network manager but i cannot use any network connection like before. It connects fine to wired, wireless and mobile broadband and gets ip addresses for dns and default gateways.

The problem is I cannot ping any ip i get "operation not permitted" trying to browse firefox reports that i dont have a working network connection so i get a page load error! Even after reinstalling wicd again I get the same response. I had enabled nat and disabled it but still not working. Am using ubuntu 9.04. Any Ideas and solution?
 Thanks in Advance.

---

### Post by ourAri on 2009-06-26
What is the contents of your /etc/network/interfaces ? In order for network manager to manage your network interfaces, all the lines in this file should be commented out.

---

### Post by superprash2003 on 2009-06-27
also post output of ifconfig from the terminal

---

### Post by heviejob on 2009-06-27
_Contents of /etc/network/interfaces_

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
 #auto eth1

 #iface eth1 inet dhcp

 #auto wlan0
 #iface wlan0 inet dhcp

and _ifconfig gives_

eth0      Link encap:Ethernet  HWaddr 00:16:36:fc:77:53  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2573 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2573 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:888141 (888.1 KB)  TX bytes:888141 (888.1 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.22.0.35  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:126 (126.0 B)  TX bytes:213 (213.0 B)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.203.1  Bcast:172.16.203.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.218.1  Bcast:192.168.218.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:2a:b0:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-7E-2A-B0-82-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


an using a usb modem to connect at this time 


when i ping yahoo.com i get

ping yahoo.com
ping: unknown host yahoo.com 


When I ping 4.2.2.2 i get

ping 4.2.2.2
PING 4.2.2.2 (4.2.2.2) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

---

### Post by heviejob on 2009-06-27
I noticed that traffic out to all interfaces connected using the network manager is being blocked because if I was pinging with the connection on and i disconnect the message on changes from "operation not permitted" to "network unreachable". I figure its something to do with iptables or some firewall thing or even dns as I had installed dnsmasq. Problem I dont know my way around iptables and natting.

---

### Post by heviejob on 2009-06-27
_Contents of /etc/network/interfaces_

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
 #auto eth1

 #iface eth1 inet dhcp

 #auto wlan0
 #iface wlan0 inet dhcp

and _ifconfig gives_

eth0      Link encap:Ethernet  HWaddr 00:16:36:fc:77:53  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2573 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2573 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:888141 (888.1 KB)  TX bytes:888141 (888.1 KB)

ppp0      Link encap:razz:oint-to-Point Protocol  
          inet addr:10.22.0.35  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:126 (126.0 B)  TX bytes:213 (213.0 B)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.203.1  Bcast:172.16.203.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.218.1  Bcast:192.168.218.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:2a:b0:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-7E-2A-B0-82-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


an using a usb modem to connect at this time 


when i ping yahoo.com i get

ping yahoo.com
ping: unknown host yahoo.com 


When I ping 4.2.2.2 i get

ping 4.2.2.2
PING 4.2.2.2 (4.2.2.2) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

---

### Post by tlois on 2009-06-27
Did you recently do updates on Ubuntu?  I have almost the exact same problem.  Had used Wicd, but after update this morning it wouldn't work.  So I reinstalled Network Manager and now cannot connect to WPA.  (That was a problem when first put out test version of latest, but that was corrected in final).  It will connect when I take it off security of WPA, but don't want to keep it that way.

Luckily, I have Eeebuntu on 10gb partition so using that for now and connects to my WPA network. 

So the question is, did you do an update recently?

---

### Post by tlois on 2009-06-27
Whoa.  I have the option to use last kernel on boot and it works now.  Hmmmm.  Do you have that option right after GRUB?

kernel that doesn't work with my WPA- 2.6.28-13       

-11 works

---

### Post by heviejob on 2009-06-27
Hi. As a matter of fact i had updated the entire system like 2 or so weeks ago. I have been working on the system all evening and its now behaving but i will check tomorrow morning if the problem persists. I uninstalled dnsmasq and put firestarter a firewall and it seemed to work. I also disabled ip forwarding. But be sure its the connections being blocked.

---

