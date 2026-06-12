---
title: "Need to have network card without an IP Address"
date: 2011-04-21
forum: Networking &amp; Wireless
---

### Post by SecSimSon on 2011-04-21
I am setting up a Snort machine and it instructs me to set up one interface without any IP Address. It instructs me to open the interfaces file using the command:

sudo vi /etc/network/interfaces


Then it instructs me to add text to the end of the file to start the second card without an IP address using these lines:

auto eth1
iface eth1 inet manual
ifconfig eth1 up


However when I do this and save the file (I open it to verify that indeed the text was saved) then restart the restart the network services - I believe I am using the right term - using the command:

sudo /etc/init.d/networking restart

While working this at another time the interface still had a DHCP supplied IP Address (from my Linksys router/switch based on the IP Address) but now I am not getting anything from ifconfig (eth1 not showing up).

Here is the text of my interfaces file:

auto eth0
iface eth0 inet static
address 192.168.37.1
netmask 255.255.255.0
network 192.168.37.0
broadcast 192.168.37.255
gateway 192.168.37.1

auto eth1
iface eth1 inet manual
ifconfig eth1 up


When I run ifconfig from the terminal window I get:

eth0      Link encap:Ethernet  HWaddr 00:0c:29:f2:96:17  
          inet addr:192.168.37.1  Bcast:192.168.37.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fef2:9617/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:715 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1509 (1.5 KB)  TX bytes:37090 (37.0 KB)
          Interrupt:19 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1057 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1057 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94573 (94.5 KB)  TX bytes:94573 (94.5 KB)


I am very new to Linus and trying to find my way but I could use some help with this. The ultimate goal is to get eth1 up without an IP address but still able to read packets off the connection.  Thanks in advance.

---

### Post by dandnsmith on 2011-04-22
To me, that last line (ifconfig ..) is wrong - just doesn't belong in the interfaces file. You could use it as a standalone command to bring the eth1 interface up.

I don't understand just what is going to handle the getting of the IP address and netmask for the interface (DHCP?)

Just to add to confusion, my interfaces file doesn't have anything for my eth0 or eth1 interfaces - those have both been set up by the 'Network Connections' admin tool.

---

### Post by nothingtolose on 2012-01-04
auto eth1
iface eth1 inet manual
ifconfig eth1 up

change to this

up ifconfig eth1 up


then restart your network interface

---

