---
title: "Lost Network Settings"
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by lengthsman on 2011-03-25
Hi,
 
My first post. I lost all connections to the internet on my Linux Box Yesterday. I have checked my broadband connection and router. OK because I am using them to sent this from my laptop. I have 2 ethernet cards - no indication of a problem with either so I suspect for reasons unknown I have lost all my network settings. The Desktop User Guide says go to the Network Settings Window. I used to have a widget on the Menu Bar which enabled me to check the settings but for some reason it vanished a month or so ago and I can't find how to get it back.
 
Any advice would be appreciated.
 
lengthsman
 
PS In the meantime I am stuck with this crummy Microsoft box the interferes with everything I try to do. Heeeeeeelp!

---

### Post by josephmills on 2011-03-25
> **lengthsman said:**
> Hi,
 
My first post. I lost all connections to the internet on my Linux Box Yesterday. I have checked my broadband connection and router. OK because I am using them to sent this from my laptop. I have 2 ethernet cards - no indication of a problem with either so I suspect for reasons unknown I have lost all my network settings. The Desktop User Guide says go to the Network Settings Window. I used to have a widget on the Menu Bar which enabled me to check the settings but for some reason it vanished a month or so ago and I can't find how to get it back.
 
Any advice would be appreciated.
 
lengthsman
 
PS In the meantime I am stuck with this crummy Microsoft box the interferes with everything I try to do. Heeeeeeelp!

could you post 
```
ifconfig 
```
```
lspci 
```
thanks

---

### Post by lengthsman on 2011-03-25
Herewith my ifconfig and lspci data:

---

### Post by lengthsman on 2011-03-25
mike@lengthsman:~$ ifconfiglo        Link encap:Local Loopback            inet addr:127.0.0.1  Mask:255.0.0.0          inet6 addr: ::1/128 Scope:Host          UP LOOPBACK RUNNING  MTU:16436  Metric:1          RX packets:60547 errors:0 dropped:0 overruns:0 frame:0          TX packets:60547 errors:0 dropped:0 overruns:0 carrier:0          collisions:0 txqueuelen:0           RX bytes:4433526 (4.4 MB)  TX bytes:4433526 (4.4 MB)mike@lengthsman:~$ lspci00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)01:00.0 Multimedia audio controller: Aureal Semiconductor Vortex 1 (rev 02)01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)mike@lengthsman:~$ Forgive my incompetent efforts to provide the above data but your site is a total mystery to a first timer!Mike

---

