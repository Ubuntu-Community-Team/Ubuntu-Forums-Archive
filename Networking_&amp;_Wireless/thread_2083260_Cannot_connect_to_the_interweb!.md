---
title: "Cannot connect to the interweb!"
date: 2012-11-11
forum: Networking &amp; Wireless
---

### Post by cyberhood on 2012-11-11
Ok, so I'm trying to revive an old computer (**HP Pavilion Entertainment PC dv9810us**) from its brick-grave. It used to be one of my family member's Windows Vista machine that after 5 years of working just fine decided to not turn on anymore. I promised them that Linux could revive it. However **neither the wired nor the wireless connections seem to want to connect to the web**. The switch for the wireless connection is moved into the 'on' position, so I don't think that is the problem. However, there does seem to be a little light there next to the wireless switch which is not coming on and I suppose is there to indicate whether or not wireless has been activated.
I discovered that **the wired hardware is NVIDIA MCP67 Ethernet** and that **the wireless is Atheros Communications Inc. AR242x/AR542x Wireless Network Adapter (PCI-Express)**. I discovered this because the hardware does seem to be recognized (the network manager told me when I live-booted PCLinuxOS) which seems strange to me... if I can find out what the hardware is from the machine itself, but it won't connect... 
In "Additional Drivers" I discovered that the NVIDIA graphics drivers have not been installed by default as they are proprietary. Would this have anything to do with the NVIDIA ethernet issue? 
The LED light next to the wireless switched lit up orange when the computer was booting up, then turned off when the booting was complete. Moving it back and forth did not cause either the light to come on or the wireless to connect.
Any help getting this old laptop revived for my family member and keeping it out of a landfill would be much appreciated.
**Thanks** in advance Ubuntu community!!!

---

### Post by mikewhatever on 2012-11-12
Can you add the output of 'lspci -nn' to the OP.

---

### Post by cyberhood on 2012-11-13
```
~ $ lspci -nn
00:00.0 RAM memory [0500]: NVIDIA Corporation MCP67 Memory Controller [10de:0547] (rev a2)
00:01.0 ISA bridge [0601]: NVIDIA Corporation MCP67 ISA Bridge [10de:0548] (rev a2)
00:01.1 SMBus [0c05]: NVIDIA Corporation MCP67 SMBus [10de:0542] (rev a2)
00:01.2 RAM memory [0500]: NVIDIA Corporation MCP67 Memory Controller [10de:0541] (rev a2)
00:01.3 Co-processor [0b40]: NVIDIA Corporation MCP67 Co-processor [10de:0543] (rev a2)
00:02.0 USB controller [0c03]: NVIDIA Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:02.1 USB controller [0c03]: NVIDIA Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:04.0 USB controller [0c03]: NVIDIA Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:04.1 USB controller [0c03]: NVIDIA Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:08.0 PCI bridge [0604]: NVIDIA Corporation MCP67 PCI Bridge [10de:0561] (rev a2)
00:09.0 IDE interface [0101]: NVIDIA Corporation MCP67 AHCI Controller [10de:0550] (rev a2)
00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP67 Ethernet [10de:054c] (rev a2)
00:0c.0 PCI bridge [0604]: NVIDIA Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:0d.0 PCI bridge [0604]: NVIDIA Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:12.0 VGA compatible controller [0300]: NVIDIA Corporation C67 [GeForce 7150M / nForce 630M] [10de:0531] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
02:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:05.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:05.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
```
Thanks :)

---

### Post by mikewhatever on 2012-11-13
A similar problem is being resolved [here]("http://ubuntuforums.org/showthread.php?t=2083228"), you might want to join in, or just watch it.

---

### Post by wildmanne39 on 2012-11-13
Hi, please try:
```
echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf
```
Then reboot.
Thanks

---

### Post by cyberhood on 2012-11-14
> **Wild Man said:**
> Hi, please try:
```
echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf
```
Then reboot.
Thanks
This worked for me. Thanks!

[SOLVED!] :guitar:

---

### Post by wildmanne39 on 2012-11-14
Your welcome!
Enjoy

---

