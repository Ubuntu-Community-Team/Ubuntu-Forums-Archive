---
title: "Hp dv2125nr wireless probs"
date: 2011-07-05
forum: Networking &amp; Wireless
---

### Post by pythonsyntax on 2011-07-05
How do i get a broadcom wireless card to work on ubuntu 11.04 and how do i find out  what driver i need to get it to work?

---

### Post by gordintoronto on 2011-07-05
The easy way: temporarily plug your computer into your router with an Ethernet cable, then run "additional drivers." It should suggest that you "activate" a Broadcom driver.

---

### Post by pythonsyntax on 2011-07-06
I have try that i see no driver that come up.

---

### Post by pythonsyntax on 2011-07-06
anyone?

---

### Post by chili555 on 2011-07-06
The hard way: open a terminal and run and post:```
lspci -nn | grep 0280
```When we know what you have, we'll be in a better position to proceed.

---

### Post by pythonsyntax on 2011-07-06
i try that command and i just got root@syntax .i try it on my other desltop samething.

---

### Post by chili555 on 2011-07-06
If the command comes back to nothing, it suggests you do not have a PCI wireless device. Is it USB?```
lsusb
sudo lshw -C network
```

---

### Post by pythonsyntax on 2011-07-06
No it not a usb 

it a  broadcom 4311  i look up on google.And i hope that helps.

---

### Post by chili555 on 2011-07-06
How about showing us all of:```
lspci -nn
```Thanks.

---

### Post by pythonsyntax on 2011-07-06
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce Go 6150] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
03:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
03:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
03:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)

---

### Post by chili555 on 2011-07-06
I'm sorry, I see no wireless device there and certainly no Broadcom.

---

### Post by gordintoronto on 2011-07-06
There's no Ethernet adapter of any kind. Is there any chance it is an Expresscard device? Is there a place to plug in an Ethernet cable?

---

### Post by chili555 on 2011-07-07
> **gordintoronto said:**
> There's no Ethernet adapter of any kind. Is there any chance it is an Expresscard device? Is there a place to plug in an Ethernet cable?Gord, I know, I almost skipped over it, too:> 00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)But it clearly isn't wireless.

---

### Post by pythonsyntax on 2011-07-07
Yes it is wireless but not sure why the wireless card not showing for.Well if there was no ethernet why would i post that output for it was from the HP laptop.THe wireless button is  not blue like it was on windows.

---

### Post by bkratz on 2011-07-07
> **pythonsyntax said:**
> Yes it is wireless but not sure why the wireless card not showing for.Well if there was no ethernet why would i post that output for it was from the HP laptop.THe wireless button is  not blue like it was on windows.



I really think you should post the lsusb, Dr. Chili asked for earlier. It just might be on an internal usb bus and not show up in the lspci posted.

---

