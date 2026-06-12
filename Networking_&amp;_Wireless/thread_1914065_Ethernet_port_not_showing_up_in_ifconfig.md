---
title: "Ethernet port not showing up in ifconfig"
date: 2012-01-23
forum: Networking &amp; Wireless
---

### Post by Travesty3 on 2012-01-23
I am new to Ubuntu, and am having trouble getting my onboard ethernet port working on a fresh install of Ubuntu 10.04 Server 32-bit. I have searched on Google, but was unable to find the answer to my problem. The motherboard is a Gigabyte G41MT-S2P. I'm not sure if it's a driver issue, but I don't know where to download a driver from. I looked on Gigabyte's website, but they say:
 
> Due to different Linux support condition provided by chipset vendors, please download Linux driver from chipset vendors' website or 3rd party website.
 
I found a few forum posts talking about getting the driver from [http://partner.atheros.com/Download.aspx?id=125](http://partner.atheros.com/Download.aspx?id=125), but that URL doesn't work. If it's a driver I need, I would appreciate a link to download it, as I've searched and have been unable to find one.
 
Here is the output of a few commands:
 
ifconfig -a:
```
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

```
 
lshw -c NET:
```
 
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:fdec0000-fdefffff ioport:df00(size=128)
 

```
 
lspci:
```
 
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
 

```

---

### Post by Travesty3 on 2012-01-24
See my solution here:
 
[http://superuser.com/questions/381804/ethernet-port-not-showing-up-in-ifconfig](http://superuser.com/questions/381804/ethernet-port-not-showing-up-in-ifconfig)

---

