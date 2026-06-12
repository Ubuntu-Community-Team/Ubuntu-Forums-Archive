---
title: "wifi not working"
date: 2013-03-21
forum: Networking &amp; Wireless
---

### Post by 87toyotafreak on 2013-03-21
hi all i have been having a problem with my pci wifi card ever since i have installed 12.04. the issue is that the wifi card is not showing up in iwconfig. but if i run lspci i can see the card is there but unclaimed. the driver should be p54pci but using modprobe p54pci is not working.
 any and all help is very much welcome thakns for taking the time to read and to help..
here is the output from terminal when lspci is run...

thomas-FK587AA-ABA-SR5605F:~$ lspci
00:00.0 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0a.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
02:00.0 VGA compatible controller: NVIDIA Corporation Device 104a (rev a1)
02:00.1 Audio device: NVIDIA Corporation HDMI Audio stub (rev a1)

---

### Post by carl4926 on 2013-03-21
I'd prefer to see
```
lspci -nnk | grep -iA2 net
```

---

### Post by 87toyotafreak on 2013-03-21
here is output


thomas-FK587AA-ABA-SR5605F:~$ lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:2a5b]
    Kernel driver in use: forcedeth
--
01:09.0 Network controller [0280]: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] [1260:3890] (rev 01)
    Subsystem: Cirrus Logic Device [1013:4201]
    Kernel modules: p54pci

---

### Post by carl4926 on 2013-03-21
```
01:09.0 Network controller [0280]: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] [1260:3890] (rev 01)Subsystem: Cirrus Logic Device [1013:4201]Kernel modules: p54pci
```Suggests the driver is loaded

---

### Post by 87toyotafreak on 2013-03-21
ok  but i still dont have lights or anything from card i haved tried everything that i can think of and that i have googled for the card hasnt worked.. it was working in my intel based box but that died yesterday so now im on my AMD box with a fresh install of 12.04

---

### Post by carl4926 on 2013-03-21
You should check it with rfkill
Make sure it's installed, then run:

```
sudo [COLOR=#000000][FONT=Droid Sans]rfkill list[/FONT][/COLOR]
```

---

