---
title: "No SSL connection"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by Terrier on 2011-02-02
Hi, since two weeks, I can not reach secured websites ([https://)]("https://%29") or the mailservers from my employer's domain. Interestingly, my wife doesn't have any problems (with her Windows system), using the same router. In my case, it also does not work when I am at work and have a networking cable plugged in. Thus, it is unlikely that the servers block my IP.

Furthermore, it is not the program. Neither my mailclients (Thunderbird or Kmail) can reach the mailservers, nor Firefox, Konqueror or rekonq can open  secured sites. But other mailservers (google, web.de, yahoo.com ...) work perfectly and also other [https://-websites](https://-websites) (e.g. online banking) do.

Oddly, it used to work sometimes after I restarted my computer. Then, it worked until I shut it down again. So, the network settings should be fine. But today, I restarted my computer about 20 times and it never worked. The mail clients keep telling me "connection refused" and Firefox "can't establish a connection to the server..."

Does anyone have an idea?

lspci

[PHP]00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
03:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)[/PHP]

ifconfig -a

[PHP]eth0      Link encap:Ethernet  HWaddr 60:eb:69:7d:40:33  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10597 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10597 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6771121 (6.7 MB)  TX bytes:6771121 (6.7 MB)

wlan0     Link encap:Ethernet  HWaddr 20:7c:8f:40:6e:5b  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::227c:8fff:fe40:6e5b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10487 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5301226 (5.3 MB)  TX bytes:1090716 (1.0 MB)
          Interrupt:16 Memory:ffffc90011098000-ffffc90011098100 [/PHP]

---

