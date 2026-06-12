---
title: "How I successfully configured my ethernet card with a static IP address"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by Lyingstone on 2008-12-30
Hi all,

I am totally new to this Ubuntu world. It took me a couple of days to figure out how to configure my ethernet card with a static IP. I just want to share with with you the experience to make the life of some newbies like me easier.

I installed Ubuntu 8.10. At the beginning the system was not connected to internet. I used Network tools to find my ethernet card, which was not configured at all.

I opened terminal and used the command "sudo ifconfig" to see the current settings for my network device. Here is the output.

eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  

          inet6 addr: fe80::219:d1ff:fe8b:9655/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:89 errors:0 dropped:0 overruns:0 frame:0

          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:33858 (33.8 KB)  TX bytes:1836 (1.8 KB)

          Memory:e3200000-e3220000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:222 errors:0 dropped:0 overruns:0 frame:0

          TX packets:222 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:13904 (13.9 KB)  TX bytes:13904 (13.9 KB)

It looked like the ethernet card was not configured. I opened the interfaces file where the configuration infor was stored. Command line: "sudo gedit /etc/network/interfaces"

There were only two lines in the file:
auto lo
iface lo inet loopb

I added the following to configure my ethernet device eth0
auto eth0
iface eth0 inet static
address 192.168.3.90
gateway 192.168.3.1
netmask 255.255.255.0
network 192.168.3.0
broadcast 192.168.3.255

I found the last two lines are quite inportant. without these two lines, the connection didn't work on my PC. So maybe true for you as well.

I also configured the DNS infor. Command line" sudo gedit /etc/resolv.conf
I added two lines in the file (two DNS servers, the latter is the alternative one)
nameserver 192.168.1.1
nameserver 192.168.1.255

Then I saved the file. I restarted networking services using the folloing command sudo /etc/init.d/networking restart. Here is the output:

Reconfiguring network interfaces...                                 [ OK ]

then I went back to Networking tools to look at the status of my eth0 device. All the settings were shown. I opened Firefox. Yeeee, Free to Surf!!! Hope this can help some of you guys.

Cheers!

---

### Post by diiphantom on 2008-12-30
Call your internet company and pay extra for static ip, lol

---

### Post by teaker1s on 2008-12-30
static ip on network is not the same as static ip on internet-clarification to previous poster:popcorn:

---

