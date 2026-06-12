---
title: "Network Problems Ubuntu Server x86 (32 bit)"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by JewFro297 on 2009-08-12
I can't connect to the internet or configure DHCP... My Linksys router has DHCP enabled.
When running the installer, DHCP configuration fails. After continuing anyway, I can not ping any sites or my router. Here is my ifconfig output:

eth1   Link encap: Ethernet HWaddr 00:30:bd:1d:68:c3
       BROADCAST MULTICAST MTV: 1500 Metric:1
       RX packets:0 Errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 Errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
        Base adress: 0x 3000

lo     link encap: Local Loopback
       inet 6 addr: :: 1/128 Scope:Host
        UP LOOPBACK RUNNING MTU: 16436 Metric1
        RX packets:61 Errors:0 dropped:0 overruns:0 frame:0
        TX packets:61 Errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes: 4388 (4.3KB) TX bytes: 4388 (4.3 KB)

And here is my interface file:
Auto lo          
iface lo inet loopback      
auto eth1        
iface eth1 inet dhcp

(I added the last two lines btw)

---

### Post by superprash2003 on 2009-08-12
post output of **sudo dhclient eth0**

---

### Post by Iowan on 2009-08-12
Just in case it might help:
[http://ubuntuforums.org/showthread.php?t=1156441]("http://ubuntuforums.org/showthread.php?t=1156441")

---

### Post by JewFro297 on 2009-08-13
> **superprash2003 said:**
> post output of **sudo dhclient eth0**

I'll post the output of eth1 too since eth0 does not appear in my system anymore

eth0:
SIOCSFADDR: No such device
eth0:ERROR while getting interface flags: No such device
eth0:ERROR while getting interface flags: No such device
Bind socket to interface: No such device



eth1:
SIOCSFLAGS: Device or rescource busy
SIOCSFLAGS: Device or rescource busy
Listening on LPF/eth1/00:30:bd:1d:68:c3
Sending on LPF/eth1/00:30:bd:1d:68:c3
recieve_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
No DHCPOFFERS recieved.
No working leases in persistent database - sleeping. 


and im sure my linksys router is set up for dhcp, I already have around 5 computers connected to it, and theres a maximum of at least ten

---

### Post by JewFro297 on 2009-08-13
HA I feel a bit lame now... It was a problem in the bios. I forgot this computer has the most touchy bios in the world, when i swapped network cards for a third time it had all these irq conflicts, so resetting the bios worked. Now my server is soon to be up and running! thanks for the help

---

### Post by Iowan on 2009-08-14
Iz'zat one of those "3's a charm" instances? Congrats - hope it stays fixed.

---

