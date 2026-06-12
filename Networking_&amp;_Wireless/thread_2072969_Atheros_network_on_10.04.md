---
title: "Atheros network on 10.04"
date: 2012-10-18
forum: Networking &amp; Wireless
---

### Post by etopsirhc on 2012-10-18
i've seen many threads about getting the drivers to work , but all of them seem to point to the same broken link. so i have to ask , does any one know how to get my network card working?

it's a 2 part problem. 
[FONT=Arial]Atheros AR8151 PCI-E Gigabit Ethernet and the
[/FONT][FONT=Arial]Atheros AR5B125 Wireless Network Adapter

if any one knows how to fix his please let me know 

because i've seen this asked for in most previous ones ...

lshw -C network
[/FONT]```

  *-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:f0300000-f033ffff ioport:3000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0200000-f027ffff memory:f0500000-f050ffff(prefetchable)

```

lspci -nn
```

00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1410]
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9990]
00:01.1 Audio device [0403]: ATI Technologies Inc Device [1002:9902]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Device [1022:1414]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Device [1022:1415]
00:07.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Device [1022:1417]
00:10.0 USB Controller [0c03]: Advanced Micro Devices [AMD] Device [1022:7812] (rev 03)
00:10.1 USB Controller [0c03]: Advanced Micro Devices [AMD] Device [1022:7812] (rev 03)
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] Device [1022:7801]
00:12.0 USB Controller [0c03]: Advanced Micro Devices [AMD] Device [1022:7807] (rev 11)
00:12.2 USB Controller [0c03]: Advanced Micro Devices [AMD] Device [1022:7808] (rev 11)
00:13.0 USB Controller [0c03]: Advanced Micro Devices [AMD] Device [1022:7807] (rev 11)
00:13.2 USB Controller [0c03]: Advanced Micro Devices [AMD] Device [1022:7808] (rev 11)
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] Device [1022:780b] (rev 14)
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] Device [1022:780d] (rev 01)
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] Device [1022:780e] (rev 11)
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] Device [1022:780f] (rev 40)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1400]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1401]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1402]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1403]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1404]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1405]
01:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)
02:00.0 Network controller [0280]: Atheros Communications Inc. Device
[168c:0032] (rev 01)
03:00.0 Class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)

```

and just in case you need more system info this is the exact model of computer i have [http://www.geeks.com/details.asp?invtid=NV52L06U-FB-R](http://www.geeks.com/details.asp?invtid=NV52L06U-FB-R)

---

### Post by chili555 on 2012-10-18
You could install 12.04 LTS and both will work out of the box.

---

### Post by etopsirhc on 2012-10-18
i would if it went for the new layout, it looks to be built for a touch screen , if i had a tablet i'd probably use 12.04 , but for a laptop or desktop i cant stand it. 

before i had linux mint 13 and it worked , but it was throwing problems at me where it wouldnt open a folder and complain about their not being a program to open it ( despite having used it less than 3 minuites prior ). after that it would go to log in but the screen after that was black with only the cursor ><

---

### Post by chili555 on 2012-10-18
You can install gnome-shell a few moments after install. Problem solved. I installed 12.10 on my laptop today in less time than I could eat lunch.

[http://www.techlw.com/2012/02/install-gnome-shell-on-ubuntu-1204.html](http://www.techlw.com/2012/02/install-gnome-shell-on-ubuntu-1204.html)

On the other hand, to install these drivers you will need to download both drivers, build-essential and several dozens of dependencies and linux-headers-generic; all without *ANY* network connection. I've helped people do it. It isn't easy and it almost never goes well in the first two or three tries.

I'll be happy to help either way.

---

### Post by etopsirhc on 2012-10-18
if the gnome shell can be run like gnome 2 ( witch i think it can from what i saw ) i'll take that over the other ( mainly cause i tried following some of your previous posts on the same problem but got stuck at installing gcc where 1 package depends on the other and the other depends on the first and neither will install properly cause the cd label is diffrent XP ) 

but yeah , i'll start the 12.04 Dl and get back to you after its installed ( will be a while due to internet speed )

---

