---
title: "No Wireless"
date: 2011-09-25
forum: Networking &amp; Wireless
---

### Post by reyno_911 on 2011-09-25
I just downloaded Ubuntu, and because i was unsure about how i would like it, i ran it with windows. After getting into it, i cannot connect to the internet wirelessly. Also, i live in the dorms at my school and i do not have a ethernet cable. It doenst show any wireless activity in the networking folder....Im a total computer noob and i have no idea where to go from here. Any help would be much appreciated.

---

### Post by bkratz on 2011-09-25
> **reyno_911 said:**
> I just downloaded Ubuntu, and because i was unsure about how i would like it, i ran it with windows. After getting into it, i cannot connect to the internet wirelessly. Also, i live in the dorms at my school and i do not have a ethernet cable. It doenst show any wireless activity in the networking folder....Im a total computer noob and i have no idea where to go from here. Any help would be much appreciated.


the first thing to do would be to drop to the terminal and copy/paste the output of the following back here, so someone familiar with your card can see what it is

lspci -nn | grep 0280

(by the way that is LSPCI in lowercase)

---

### Post by reyno_911 on 2011-09-25
cdr@ubuntu:~$ lspci 
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1) 
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2) 
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2) 
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2) 
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) 
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) 
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) 
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2) 
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2) 
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) 
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) 
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) 
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) 
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
02:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350] 
02:00.1 Audio device: ATI Technologies Inc RV710/730 

That's what i came back with.....Also, i dont have an internal wireless card. I have a USB wireless adapter. IDK if thats something i should have brought up earlier or not

---

### Post by bkratz on 2011-09-25
> **reyno_911 said:**
> cdr@ubuntu:~$ lspci 
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1) 
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2) 
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2) 
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2) 
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) 
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) 
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) 
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2) 
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2) 
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) 
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) 
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) 
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) 
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
02:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350] 
02:00.1 Audio device: ATI Technologies Inc RV710/730 

That's what i came back with.....Also, i dont have an internal wireless card. I have a USB wireless adapter. IDK if thats something i should have brought up earlier or not


I should have thought about that too! Anyway, copy/paste the output of 

lsusb

(LSUSB in lowercase) back here.

---

