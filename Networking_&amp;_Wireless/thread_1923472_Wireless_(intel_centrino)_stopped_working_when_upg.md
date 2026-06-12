---
title: "Wireless (intel centrino) stopped working when upgrading my Linux kernel"
date: 2012-02-10
forum: Networking &amp; Wireless
---

### Post by haisenthil on 2012-02-10
[IMG]http://mail.yimg.com/a/a/stationery/static/liam_fetch_lb.gif[/IMG] 
[FONT=arial, helvetica, sans-serif][SIZE=2][COLOR=#333333][COLOR=#333333][FONT=arial]HI

I have Ubuntu 11.10 version with Linux kernel 3.0.14 in my Lenova Laptop that has Intel Centrino 6200 as wireless interface.. The wlan works fine and am able to connect to Internet.
But after I upgraded my Linux  kernel to 3.2.2 (or 3.2.5), it does not work. 


<Settings>--><Network> does not list 'wireless' at all. 
lshw -c Network says  'it is UNCLIAMED"

 Have any one of you seen this issue? 
Any pointers?

The output of:

# lshw -C network
[IMG]http://mail.yimg.com/a/a/stationery/static/liam_fetch_lb.gif[/IMG] 
[FONT=arial, helvetica, sans-serif][SIZE=2][COLOR=#333333][COLOR=#333333][FONT=arial]      resources: irq:41 memory:f2400000-f241ffff memory:f2425000-f2425fff ioport:1820(size=32)
  *-network  UNCLAIMED
       description: Network controller
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 35
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f2000000-f2001fff
asnhost@asnhost-ThinkPad-T410:~$  


 sudo lspci -v |more


03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
    Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f2000000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 58-94-6b-ff-ff-7b-02-78




[/FONT][/COLOR][/COLOR][/SIZE][/FONT]

Thanks
=Senthil

    
[/FONT][/COLOR][/COLOR][/SIZE][/FONT]

---

### Post by tuxonapogostick on 2012-02-11
I have a similar problem: my internal wireless RT3090 is not working with 3.0.0.14 and 3.0.0.15 kernels. I guess problem we're experiencing is not wireless chip type specific.
*I take it back. Turns out the problem was due to some modules I blacklisted which were problematic before but now they are doing fine, and wireless is working.*

---

### Post by albank on 2012-04-27
@[haisenthil]("http://ubuntuforums.org/member.php?u=1548971") I have an identical problem. After upgrading to ubuntu 12.04LTS which uses kernel 3.2, my wireless n-6200 is not recognized. It was fine before on kernel 3.0. It works fine on windows 7. Seems like a driver issue. Any help would be appreciated.

>lshw -C network

*-network UNCLAIMED
       description: Network controller
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 35
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f2400000-f2401fff


/////////////////////////////////////////////////////////////////////////

> sudo lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series/3400 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

---

### Post by chili555 on 2012-04-27
Please post:```
rfkill list all
sudo modprobe iwlwifi
dmesg | grep iwl
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by albank on 2012-04-27
I resolved this issue. Looks like the iwlwifi driver was blacklisted. I had to edit /etc/modprobe.d/blacklist-local.conf and put a comment in front of "blacklist iwlwifi"

---

### Post by chili555 on 2012-04-27
Awesome! Glad it's working.

---

