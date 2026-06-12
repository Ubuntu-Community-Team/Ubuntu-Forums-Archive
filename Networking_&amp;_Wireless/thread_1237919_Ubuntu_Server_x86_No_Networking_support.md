---
title: "Ubuntu Server x86 No Networking support"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by JewFro297 on 2009-08-11
Hey can anyone help me? I just installed Ubuntu server edition on an old hp pavilion from 1998. At first I found out the network card was unsupported, so I swapped out a supported one. But the same problem exists. I can't connect to the internet. (Ping says it doesn't know the host)

Tell me the information you need to help me further please
(I'm not brand new to Ubuntu or Linux... But I'm definitely no expert.)

---

### Post by nandemonai on 2009-08-11
Please post your /etc/network/interfaces file.

The output from ifconfig -a would also help. :)

---

### Post by JewFro297 on 2009-08-11
Auto lo          
iface lo inet loopback      
auto eth0        
iface eth0 inet dhcp


thats the interfaces file (I added the last two lines but it didn't do anything)

Ill get the ifconfig in a few minutes (gotta write it down then bring it up stairs)

---

### Post by JewFro297 on 2009-08-11
> **JewFro297 said:**
> Auto lo          
iface lo inet loopback      
auto eth0        
iface eth0 inet dhcp


thats the interfaces file (I added the last two lines but it didn't do anything)

Ill get the ifconfig in a few minutes (gotta write it down then bring it up stairs)


Heres the ifconfig -a:

eth1   Link encap: Ethernet HWaddr 00:30:bd:1d:68:c3
BROADCAST MULTICAST MTV: 1500 Metric:1
RX packets:0 Errors:0 dropped:0 overruns:0 frame:0
TX packets:0 Errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Base adress: 0x 3000

that was hand writen then typed so there might be slight errors, (capitilization and such)
and the lo loopback part will be added in a few more minutes

---

### Post by JewFro297 on 2009-08-11
> **JewFro297 said:**
> Heres the ifconfig -a:

eth1   Link encap: Ethernet HWaddr 00:30:bd:1d:68:c3
BROADCAST MULTICAST MTV: 1500 Metric:1
RX packets:0 Errors:0 dropped:0 overruns:0 frame:0
TX packets:0 Errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Base adress: 0x 3000

that was hand writen then typed so there might be slight errors, (capitilization and such)
and the lo loopback part will be added in a few more minutes

And heres the lo
lo   link encap: Local Loopback
inet 6 addr: :: 1/128 Scope:Host
UP LOOPBACK RUNNING MTU: 16436 Metric1
RX packets:61 Errors:0 dropped:0 overruns:0 frame:0
TX packets:61 Errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes: 4388 (4.3KB) TX bytes: 4388 (4.3 KB)

---

### Post by Iowan on 2009-08-12
There's probably a reason the simple solution won't work, but...
since **ifconfig** shows eth1 (and not eth0), try changing your */etc/network/interfaces* file to reference eth1 instead of eth0. It might be possible to edit */etc/udev/rules.d/70-persistent-net.rules* so the interface is labeled eth0, but try the easy way first.

---

### Post by nandemonai on 2009-08-13
Yup, that would be the problem. eth0 is your old card, even if it's no longer in the machine (it remembers the MAC address).

You can edit /etc/network/interfaces to use eth1 and you should be good.

As Iowan said you can reset it by editing/deleting /etc/udev/rules.d/70-persistent-net.rules

For example: 

[http://yoopergeek.blogspot.com/2007/07/vmware-loosing-eth0-after-youve-copied.html](http://yoopergeek.blogspot.com/2007/07/vmware-loosing-eth0-after-youve-copied.html)

---

### Post by JewFro297 on 2009-08-13
I changed the interfaces file to use eth1 already, but it didn't work. I'll try the other way next, any other ideas?

edit: I now have changed eth1 to eth0, and still no luck.

---

### Post by Iowan on 2009-08-13
Did you restart networking (or reboot) after changing the */etc/network/interfaces* file? You could also try manually activating via **dhclient ethX** (depending on which interface is configured).

---

### Post by JewFro297 on 2009-08-13
> **Iowan said:**
> Did you restart networking (or reboot) after changing the */etc/network/interfaces* file? You could also try manually activating via **dhclient ethX** (depending on which interface is configured).
Restart didn't work, and dhclient eth0 displayed: 

eth0:
SIOCSFLAGS: Device or rescource busy
SIOCSFLAGS: Device or rescource busy
Listening on LPF/eth0/00:30:bd:1d:68:c3
Sending on LPF/eth0/00:30:bd:1d:68:c3
recieve_packet failed on eth1: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
No DHCPOFFERS recieved.
No working leases in persistent database - sleeping.

---

### Post by Iowan on 2009-08-13
Confirm cable connection - **dhclient** acts like neither card is connected.

---

### Post by JewFro297 on 2009-08-13
I tried connecting to the one I use upstairs... no luck, Im trying a few more network cards just to be sure... any more ideas?

---

### Post by JewFro297 on 2009-08-13
HA I feel a bit lame now... It was a problem in the bios. I forgot this computer has the most touchy bios in the world, when i swapped network cards for a third time it had all these irq conflicts, so resetting the bios worked. Now my server is soon to be up and running! thanks for the help

---

