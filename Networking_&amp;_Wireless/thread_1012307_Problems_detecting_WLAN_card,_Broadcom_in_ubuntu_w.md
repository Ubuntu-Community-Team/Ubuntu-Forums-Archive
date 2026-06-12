---
title: "Problems detecting WLAN card, Broadcom in ubuntu with a pavilion dv9000"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by fep on 2008-12-15
Hello everybody. I have some serious problems to get the wireless adapter to work in ubuntu 8.10 on HP pavilion dv9000. I have tried a lot of different things like ndiswrapper(wich i never got to work) and linux-backports-modules. I have read a lot in ubuntuforum, and i cannot find any solution that works for me. I have the network icon in my taskbar, but there is noe wireless network option there. When i run lspci and lsusb i cannot find any wireless adapter at all. I am sure that there is at broadcom wireless card in the computer, i have tried b43, firmware and drivers, nothing works. When i write wlanconfig it says no wireless network. I am stuck and i dont know what to do, i have worked with this problem for four days now. One of the big problems is that i have no other way to connect that dv9000 to the net beside the wireless signals to get drivers/firmware, and i have to use this laptop to get deb files and such, i have to copy it into a memory stick and copy it over, that is a lot of work when there is missing packages to install packages. Is there any easy solution for this problem? Maybe all inn one packages with drivers/firmware/wireless things that i need? Please help me. Maybe someone got any tips?

---

### Post by fep on 2008-12-15
here is my lspci :

fep> trond@trond-laptop:~$ lspci
<fep> 00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
<fep> 00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
<fep> 00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
<fep> 00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
<fep> 00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
<fep> 00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
<fep> 00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
<fep> 00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
<fep> 00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
<fep> 00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
<fep> 00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
<fep> 00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
<fep> 00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
<fep> 00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
<fep> 00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
<fep> 00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
<fep> 00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
<fep> 00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
<fep> 00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
<fep> 00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
<fep> 00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
<fep> 00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
<fep> 00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
<fep> 00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
<fep> 00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
<fep> 00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
<fep> 05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
<fep> 07:05.0 FireWire (IEEE 1394): Ricoh Co 
<fep> 07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
<fep> 07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
<fep> 07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
<fep> 07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
<fep> trond@trond-laptop:~$

---

### Post by Ayuthia on 2008-12-15
You might want to check out this [link]("http://forum.notebookreview.com/showthread.php?t=233974").  I had this issue with my laptop and had to send my laptop to HP to get repaired.  Fortunately, it was covered by their limited warranty.

---

### Post by fep on 2008-12-18
I solved this problem buying a new usb wireless network card (:

---

