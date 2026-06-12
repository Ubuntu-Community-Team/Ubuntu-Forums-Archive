---
title: "Auto Ethernet Won't Work"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by LVCNSOL on 2009-05-12
Sorry if this has been posted before, I have Googled and searched but nothings helping.

I have xubuntu on an old PC, but I cannot get the Ethernet to work. I have it connected to my router and the router light comes on and the light on the PC comes on, then i select auto etho or so, it will search a bit, but then say disconnected.

ifconfig:
> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:21:c2:ff:ff  
	inet6 addr: fe80::200:21ff:fec2:ffff/64 Scope:Link
      UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
      RX packets:0 errors:0 dropped:7395 overruns:0 frame:14790
      TX packets:0 errors:14 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000 
      RX bytes:0 (0.0 B)  TX bytes:6750 (6.7 KB)
      Interrupt:5 Base address:0x4800 

lo    Link encap:Local Loopback  
      inet addr:127.0.0.1  Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING  MTU:16436  Metric:1
      RX packets:10 errors:0 dropped:0 overruns:0 frame:0
      TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0 
      RX bytes:460 (460.0 B)  TX bytes:460 (460.0 B)


---

### Post by spacesamurai on 2009-05-12
By default, the [auto eth0] is set as to get its IP from a DHCP server. I see your output and no IP address. Do you have a DHCP server set up on the router?  Or is there a DHCP server to which the PC can connect to?

---

### Post by LVCNSOL on 2009-05-12
I have my main machine with XP on it, then theres a machine in my sisters room also XP, they both networked through the router and both work perfectly fine. Don't know if thats relevant? 

I have no idea if theres a DHCP server on the router. I'm am always clueless with networking. :redface:

---

### Post by coutts99 on 2009-05-12
Post the output of -:

> sudo dhclient eth0

---

### Post by LVCNSOL on 2009-05-12
sudo dhclient eth0

> Listening on LPF/eth0/00:00:21:c2:ff:ff
Sending on   LPF/eth0/00:00:21:c2:ff:ff
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by LVCNSOL on 2009-05-12
Anyone else who might be able to help? 

Thanks :)

---

### Post by Iowan on 2009-05-12
My laptop suddenly decided to pull the same trick.  The Windows side (it's a dual-boot) works fine, the Ubuntu side won't get DHCP address.  Short term (until I can fix it properly)  I set it up with static address and manually set DNS server in /etc/resolv.conf.

---

