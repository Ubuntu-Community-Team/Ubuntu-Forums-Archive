---
title: "Wired network!"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by LinRulz on 2010-11-19
Hi! I have burned a Ubuntu 10.10 live image on a cd and when I boot and Ubuntu starts I cannot use internet because it says: "Wired network........"
I have a motherboard with GeForce 7025 / nForce 630a chipset.
Please help me to resolve this issue.


P.S.: Excuse my english if I wrong somewhere. ;)

---

### Post by chili555 on 2010-11-19
Your English is just fine; no worries. We need to know more about your wired ethernet card. Please open Applications > Accessories > Terminal and post:```
lspci -nn
```Thanks.

---

### Post by LinRulz on 2010-11-19
I have this: CPU: AMD Sempron LE-140
             MB: Asrock N68C-S UCC
             ( For the model of graphics and LAN, etc visit [this](http://www.asrock.com/mb/overview.asp?Model=N68C-S%20UCC&cat=Specifications) ).

---

### Post by chili555 on 2010-11-19
I'm sorry, I need the *lspci -nn* matching this: Realtek PHY RTL8201EL. I can't do much without the pci.id numbers.

---

### Post by LinRulz on 2010-11-19
Take a look:


```
00:00.0 RAM memory [0500]: nVidia Corporation MCP61 LPC Bridge [10de:03e2] (rev a1)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP61 LPC Bridge [10de:03e1] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP61 SMBus [10de:03eb] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [10de:03f5] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f1] (rev a3)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f2] (rev a3)
00:04.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI bridge [10de:03f3] (rev a1)
00:05.0 Audio device [0403]: nVidia Corporation MCP61 High Definition Audio [10de:03f0] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP61 IDE [10de:03ec] (rev a2)
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
00:08.0 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:08.1 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:09.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e8] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:0d.0 VGA compatible controller [0300]: nVidia Corporation C61 [GeForce 7025 / nForce 630a] [10de:03d6] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control [1022:1204]

```

---

### Post by chili555 on 2010-11-19
Oh, wonderful! There is not a thing in there that's an ethernet card. Let's also see:```
lsusb
sudo lshw -C network
```We'll find it, I hope.

---

### Post by LinRulz on 2010-11-20
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0951:1625 Kingston Technology 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Kingston --- > Is my usb stick.

I typed what you said and at the first command I got what is upper and at the second command I got nothing.

---

### Post by chili555 on 2010-11-20
May I assume the computer runs Windows? Does the ethernet adapter work correctly in Windows? I wonder if Windows has left the ethernet adapter turned off. Are there settings in the computer's BIOS that might help? Typically, Wake-on-LAN leaves the ethernet adapter turned on so it may respond to network messages when the computer is shut down. I'd make sure Wake-on-LAN is enabled both in the BIOS and in the settings in Windows.

As it stands now, there is no evidence whatever of any ethernet device. I know of no way to start a device that the operating system doesn't even know about.

Please check the settings in the BIOS and Windows and post back to let us, including the searchers, what you find.

---

### Post by LinRulz on 2010-11-20
1. Yes! I run Windows on my computer.
2. Yes! The ethernet adapter works corectly in Windows.

In the BIOS Wake-On-LAN is turned OFF.
                
In Ubuntu when I click on the network icon in the top bar I see something with vth0 ( or something with _th0 ).

---

### Post by chili555 on 2010-11-20
If it is eth0, then it sounds like it's actually working. Please post:```
ifconfig
```Thanks.> In the BIOS Wake-On-LAN is turned OFF.Please turn it on, as well as any such settings in Windows so we can see if your ethernet adapter appears in lspci -nn.

---

### Post by Crashjuh on 2010-11-26
The Asrock N68C-GS UCC is fully supported under Ubuntu 10.04 installed.

lspci -nn shows:

00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)

I don't try the live-cd

---

