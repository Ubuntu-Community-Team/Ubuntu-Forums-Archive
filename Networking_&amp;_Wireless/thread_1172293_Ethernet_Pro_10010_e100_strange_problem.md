---
title: "Ethernet Pro 100/10 e100 strange problem"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by Thanatios on 2009-05-28
Greetings,

About 3 days ago I installed Xubuntu on an old Laptop collecting dust I found. I wanted to ask for help on my Ethernet Pro 100 network card.

My PC system is:
Armada E500
600 MHz
128 MB DDR RAM
15 GB HDD
CD-Rom, Floppy, USB (1.1?)
Bios dates to 1999
Xubuntu

The problem is that when I connect it to an wired internet connection it seems to connect (atleast thats what the network icon is telling me). But in fact I don't have any internet in firefox or elsewhere on the system.

My ifconfig:
eth0
link encap:Ethernet HWaddr 00:d0:59:2c:87:95
inet6 addr: fe80: :2d0:59ff:fe2c:8795/64 scope:link
UP BROASDCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1705 errors:0 dropped:0 overruns:0 frame:0 
TK packets:28 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen: 1000
RX bytes: 108514 (105.9 KB) TX bytes:5451 (5.3 KB)

eth0:avahi
link encap:Ethernet HWaddr 00:d0:59:2c:87:95
inet addr:169.254.7.12 Bcast:169.254.255.255 mask:255.255.0.0
UP BROASDCAST RUNNING MULTICAST MTU:1500 Metric:1

lo
Link encap: Ethernet HWaddr 00:d0:59:2c:87:95
inet addr:1127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1705 errors:0 dropped:0 overruns:0 frame:0 
TK packets:28 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen: 0
RX bytes:1592 (1.5 KB) TX bytes:1592 (1.5 KB)

Connection Information tells:
Interface: Ethernet (eth0)
Speed: 100 Mb/s
Driver: e100

All the adresses mark 0.0.0.0

Can anyone help me sort this out please?

Thanks in advance!

---

### Post by dandnsmith on 2009-05-28
[i]"eth0:avahi
link encap:Ethernet HWaddr 00:d0:59:2c:87:95
inet addr:169.254.7.12 Bcast:169.254.255.255 mask:255.255.0.0"[/i]

That IP address says that the DHCP isn't getting a proper address - it's a default used where the acquisition hasn't worked.

I assume that you may be connecting to a (wireless) router, and it isn't passing the security reequirements.

Apart from allocating an IP address by hand, I don't know what to advise

---

### Post by Thanatios on 2009-05-28
Thanks for your fast answer!

Well its quite strange since by far as I know, there is no wireless support for this laptop. Correct me if I'm wrong.

It seems that there is an option to connect to "802.1X Protected Network". But I have to configure it all by myself. And the problem is that my internet connection is named: Unknown Internet. I don't know if thats an idea to try then?

---

### Post by superprash2003 on 2009-05-28
in your terminal type** sudo dhclient eth0** and post output

---

### Post by Thanatios on 2009-05-30
Its quite hard for me to typ it all over, do you really need the information?

---

### Post by superprash2003 on 2009-05-30
save output to a file ,copy via pen drive and post here..  your eth0 isnt getting an ip address. so the above command tells ubuntu to look for DHCP OFFERS from your network

---

