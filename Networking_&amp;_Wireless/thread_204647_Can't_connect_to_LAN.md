---
title: "Can't connect to LAN"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by albinoarmadillo on 2006-06-27
Hi,
I'm an Ubuntu beginner and have installed 6.06 on a Dell L800r. I'm trying to configure the network settings in order to use the local LAN. As yet, I've been unable to even ping machines on the same network, let alone use firefox. I initially tried using DHCP as is normal on the network but don't seem to be assigned an IP - the following is the ifconfig output:

eth0      Link encap:Ethernet  HWaddr 00:80:AD:06:A6:F2
          inet6 addr: 2001:770:10:200:280:adff:fe06:a6f2/64 Scope:Global
          inet6 addr: fe80::280:adff:fe06:a6f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16691 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1484732 (1.4 MiB)  TX bytes:6240 (6.0 KiB)
          Interrupt:10 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8428 (8.2 KiB)  TX bytes:8428 (8.2 KiB)

I then used a static IP address from a disconnected machine but no joy either - this is the ifconfig output:

eth0      Link encap:Ethernet  HWaddr 00:80:AD:06:A6:F2
          inet addr:134.226.48.47  Bcast:134.226.255.255  Mask:255.255.0.0
          inet6 addr: 2001:770:10:200:280:adff:fe06:a6f2/64 Scope:Global
          inet6 addr: fe80::280:adff:fe06:a6f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2566272 (2.4 MiB)  TX bytes:9452 (9.2 KiB)
          Interrupt:10 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8428 (8.2 KiB)  TX bytes:8428 (8.2 KiB)

Any ideas on how to overcome the problem are very much appreciated.
Thanks.

---

### Post by x64Jimbo on 2006-06-27
Can you show us some commands you've run and their outputs (besides ifconfig)?
More information is useful.

---

### Post by albinoarmadillo on 2006-06-27
I'm afraid I haven't tried too many other commands - I'm using the networking and network tools guis to test things out.  
lspci -tv gives:

0000:00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
0000:01:09.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
0000:01:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
0000:01:0b.0 Communication controller: Conexant HCF 56k Data/Fax Modem (rev 08)
paul@suttonpUbuntu:~$ lspci -tv
-[00]-+-00.0  Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub]
      +-01.0  Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]
      +-1e.0-[01]--+-09.0  Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet
      |            +-0a.0  Ensoniq ES1371 [AudioPCI-97]
      |            \-0b.0  Conexant HCF 56k Data/Fax Modem
      +-1f.0  Intel Corporation 82801AA ISA Bridge (LPC)
      +-1f.1  Intel Corporation 82801AA IDE
      +-1f.2  Intel Corporation 82801AA USB
      \-1f.3  Intel Corporation 82801AA SMBus

Could you suggest any other info that might be useful?

---

### Post by x64Jimbo on 2006-06-27
Well, we already know that your interfaces are connected, so that shouldn't be an issue. You should try running this:
sudo ifconfig eth0 up
sudo dhclient eth0
That should grab an IP.

---

### Post by mips on 2006-06-27
Your issue is probably related to the Tulip network chipset you have.

[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

Do a search in these forums for "Tulip"

---

### Post by albinoarmadillo on 2006-06-27
Afraid I had no joy with that either - this is the output:

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:80:ad:06:a6:f2
Sending on   LPF/eth0/00:80:ad:06:a6:f2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Thanks for your help - any other ideas as to what might be wrong?

---

### Post by mips on 2006-06-27
Uhm, I posted the link to a solution to your problem, does it not work ?

---

### Post by takakia on 2006-06-28
I am also having a similar problem.  The connection was working fine, but when I downloaded and installed the rp-pppoe client for ADSL connection ( I use ADSL at home and LAN at office) I cannot connect to the internet from LAN.  

I truid deactivating the eth0 connection and activating it again from the graphical interface (System-Administration-Networking), but still I cannot connect to the internet via LAN.

---

### Post by bforbes on 2006-06-28
What kind of network is it? Do you administer the routers and switches? Also, please use code tags for output.

---

### Post by takakia on 2006-06-28
No I don't have any routers.  The LAN in office is how I connect to the internet.  I just connect to a wall outlet with DHCP and it worked pefectly until yesterday when I installed rp-pppoe

The output of ifconfig is here
```

eth0 Link encap:Ethernet HWaddr 00:0A:E4:A1:6B:1B
          inet addr:147.8.76.117 Bcast:147.8.76.255 Mask:255.255.255.0
          inet6 addr: 2002:9308:80aa:4:20a:e4ff:fea1:6b1b/64 
Scope:Global
          inet6 addr: fec0::4:20a:e4ff:fea1:6b1b/64 Scope:Site
          inet6 addr: 2001:ce0:2:111:20a:e4ff:fea1:6b1b/64 Scope:Global
          inet6 addr: fe80::20a:e4ff:fea1:6b1b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          RX packets:9430 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2078582 (1.9 MiB) TX bytes:6077 (5.9 KiB)
          Interrupt:10 Base address:0xc800 eth1 Link encap:Ethernet 
HWaddr 00:0E:35:B9:28:0E
          UP BROADCAST MULTICAST MTU:1500 Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xe000 Memory:e0204000-e0204fff lo 
Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5056 (4.9 KiB) TX bytes:5056 (4.9 KiB)

```

---

### Post by albinoarmadillo on 2006-06-28
[QUOTE=mips]Uhm, I posted the link to a solution to your problem, does it not work ?[/QUOTE]


Hi Mips,
sorry about the delayed reply.
I tried that solution but didn't have any luck with it. 
Thanks anyway.

---

