---
title: "wireless does not work"
date: 2011-01-30
forum: Networking &amp; Wireless
---

### Post by kitoisara on 2011-01-30
ok i have yet to get my wireless driver to work and thats one thing that i need the most so i need a little help here. this is what i have in my computer 

 lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

---

### Post by grahammechanical on 2011-01-30
Ok, so you have a Broadcom BCM4312 wireless adapter. What have you done to try to set up a wireless connection? Have you read the section on the Internet and Networking in the Ubuntu Help Centre? What version of Ubuntu do you have? You need to help us to help you.

Regards.

---

### Post by kitoisara on 2011-01-30
well it really want even install a driver when i got to additional drivers there are two drivers there a B43 wireless driver and a STA wireless driver and i try to install one or the other then it says one of them is installed but i cant connect to any wifi so i dont know i have 10.10 ubuntu is there anything i can type in the terminal to paste here that can be looked out that will help out?

---

### Post by c2tarun on 2011-01-30
> **kitoisara said:**
> well it really want even install a driver when i got to additional drivers there are two drivers there a B43 wireless driver and a STA wireless driver and i try to install one or the other then it says one of them is installed but i cant connect to any wifi so i dont know i have 10.10 ubuntu is there anything i can type in the terminal to paste here that can be looked out that will help out?

ok this may not work, but its worth giving a try.
U mentioned you are getting two drivers in additional drivers and you already installed one.
Deactivate it, install the other, switch off wireless, remove LAN cable and reboot. When ubuntu starts then switch on wifi and wait for few minutes.

---

### Post by Bucky Ball on 2011-01-30
Plug in an ethernet cable, get online and try again. You need to be online to download the firmware when installing the drivers.

```
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```This Broadcom card should be a two click process but you need to be online with a cable to do it. Catch 22 situation, really. ;)

---

### Post by kitoisara on 2011-01-30
yeah iv already tryed all that iv been switching back and forth restarting and everything and its still not working, i know it will work iv tryed ubuntu before for and everything installed fine then i went back to windows for a while and i came back to ubuntu so i downloaded the alternate iso again and re installed ubuntu and it didnt work like it did the first time i tried ubuntu

---

### Post by nm_geo on 2011-01-30
> **kitoisara said:**
> yeah iv already tryed all that iv been switching back and forth restarting and everything and its still not working, i know it will work iv tryed ubuntu before for and everything installed fine then i went back to windows for a while and i came back to ubuntu so i downloaded the alternate iso again and re installed ubuntu and it didnt work like it did the first time i tried ubuntu

try this in terminal

```
rfkill list
```

---

### Post by kitoisara on 2011-01-31
hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

---

### Post by AlexQM on 2011-02-02
Once you have enabled one of the drivers (from the two listed in Additional Drivers), open the terminal and type:

```
ifconfig
```

You should see some thing like this:

```
alex@alex-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:66:78:bb:c0  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:66ff:fe78:bbc0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3558 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2985 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4087574 (4.0 MB)  TX bytes:363303 (363.3 KB)
          Interrupt:46 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0e:2e:43:9a:eb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

If wlan0 is not there, try typing in:

```
sudo ifconfig wlan0 up
```

Then check ifconfig again to see if it is up.

Alex

---

