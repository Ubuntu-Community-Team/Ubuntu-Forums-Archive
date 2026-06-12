---
title: "Acer 5520 Wireless randomly stops working"
date: 2010-04-28
forum: Networking &amp; Wireless
---

### Post by Metal_Koola on 2010-04-28
My Acer's Wireless randomly stops working until you fully shut down and  start the computer.(Not Restart but Shutdown->Powebutton) I am using  Ubuntu 10.04 Lucid.

I am wondering if anyone knows why it would stop working properly,  and/or how to fix it?

And since this is a off and on problem I might not be able to provide  details immediately from time of crash, since I need my computer on the  wireless.

One symptom that really stands out is that the cooling  fan is spinning as fast as it possibly can and processor usage is  spiking around 80/200 on a process called phy0.(relevancy unknown)

Sorry, As I was typing this post on my other computer, my  laptop crashed and I lost the lshw -C Network output I had. If asked to,  I will post the one from when it is working. Also I will post any other  info you need from when I can.

---

### Post by Metal_Koola on 2010-05-02
OK, It did it again and I grabbed the lspci and the lshw -C Network in respective order:
```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7000M / nForce 610M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

``````
  *-network
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:e2:d1:83
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:27 memory:d0887000-d0887fff ioport:30f8(size=8) memory:d0888800-d08888ff memory:d0888400-d088840f
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:e1:2a:65:1d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:d0400000-d040ffff
```

---

### Post by andradelipe on 2010-05-15
You're using lucid? Your video res is in 1280x1024?  how can you put this nVidia 7000m to work?

my wireless is normal here.

my cd-rom is dead. the bios don't recognize it anymore...

---

### Post by Metal_Koola on 2010-05-16
> **andradelipe said:**
> You're using lucid? Your video res is in 1280x1024?  how can you put this nVidia 7000m to work?

my wireless is normal here.

my cd-rom is dead. the bios don't recognize it anymore...
Lovely Hijack. :p

Download the package nvidia-current. It should work then.

---

### Post by cabez0n on 2010-06-01
> **Metal_Koola said:**
> My Acer's Wireless randomly stops working until you fully shut down and  start the computer.(Not Restart but Shutdown->Powebutton) I am using  Ubuntu 10.04 Lucid.

I am wondering if anyone knows why it would stop working properly,  and/or how to fix it?

And since this is a off and on problem I might not be able to provide  details immediately from time of crash, since I need my computer on the  wireless.

One symptom that really stands out is that the cooling  fan is spinning as fast as it possibly can and processor usage is  spiking around 80/200 on a process called phy0.(relevancy unknown)

Sorry, As I was typing this post on my other computer, my  laptop crashed and I lost the lshw -C Network output I had. If asked to,  I will post the one from when it is working. Also I will post any other  info you need from when I can.

I am also expiriencing the wifi breaking up every once in awhile on teh same laptop (Acer Aspire 5520). 
The only solution i've found so far is to restart the laptop. 

Are you also having problems on booting ? Sometimes my laptop will freeze on the gdm login screen. I also have to restart the laptop to be able to log in. 

Very weird issues.

---

### Post by g1zmog0 on 2010-06-17
I own the same laptop with Ubuntu 9.04, I believe its due to the pci express slots, or the wifi cards in the slots themselves overheating. I usually have to swap out cards, or just turn my wifi off and wait for it to cool down. It happened more when I had 2 wifi cards taking up both of the slots, I'd always have to remove them both then put them back in later.

I usually just turn my wifi off when im not using it now, which is tedious, but I never have problems after that unless the card is running for a long while (a day or so on avg).

---

### Post by Metal_Koola on 2010-06-21
Well, it seems that the security level of the router is effecting how bad it is. Also, blow some compressed air into the vent ports it seems to lower the running temp a load. Also I am running Ubuntu 10.10 now.

If you are experiencing the probelm, do this when it crashes:
acpi -V
If the temperature there is extremely high, you need to reboot because the wireless overheated.


On a side note, my CD drive is dead too, even BIOS won't recognize it.

---

### Post by javad-r on 2010-08-30
> **Metal_Koola said:**
> My Acer's Wireless randomly stops working until you fully shut down and  start the computer.(Not Restart but Shutdown->Powebutton) I am using  Ubuntu 10.04 Lucid.

I am wondering if anyone knows why it would stop working properly,  and/or how to fix it?

And since this is a off and on problem I might not be able to provide  details immediately from time of crash, since I need my computer on the  wireless.

One symptom that really stands out is that the cooling  fan is spinning as fast as it possibly can and processor usage is  spiking around 80/200 on a process called phy0.(relevancy unknown)

Sorry, As I was typing this post on my other computer, my  laptop crashed and I lost the lshw -C Network output I had. If asked to,  I will post the one from when it is working. Also I will post any other  info you need from when I can.

Hi, I have the same problem and I have found a temporary solution for that.
Every time my wireless stops working I'm just entering these commands:
$ sudo rmmod iwlagn
$ sudo rmmod iwlcore
$ sudo modprobe iwlcore
$ sudo modprobe iwlagn

and it gets back to work.

---

### Post by sp0 on 2011-01-25
Well, I got the same problem on Ubuntu 10.10. I don't think it's a heat issue, since it works without any problem in Vista.

Googling around I see many others having the "Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)" describe the same problem, but no solution found yet.

It must be a driver problem?

---

### Post by vtired on 2011-01-29
> **g1zmog0 said:**
> 
I usually just turn my wifi off when im not using it now, which is tedious, but I never have problems after that unless the card is running for a long while (a day or so on avg).

Plesae, how do you switch off wifi? Need to do it for battery economy when I am not using wifi.

---

### Post by knappster99 on 2011-02-07
Noob here with the same laptop and problems.  This all started after I upgraded to 10.04.  I feel the same because when my wireless crashes, everything chugs for a second and then audio is choppy thereafter.  Also, I've tried many solutions but cruising on my iphone while my laptop won't connect isn't fixing the problem.

---

### Post by amrdarwish1975 on 2011-05-09
I have same issue w/ my Acer Aspire 5520 - ubuntu v11. After using my Wifi for couple of hours it get disconnected w/ no apparent reason. Based on above findings, most probably it is is a driver issue. Any support?

---

