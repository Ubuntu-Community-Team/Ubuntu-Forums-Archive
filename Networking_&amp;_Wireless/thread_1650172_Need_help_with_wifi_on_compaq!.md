---
title: "Need help with wifi on compaq!"
date: 2010-12-21
forum: Networking &amp; Wireless
---

### Post by duttyg on 2010-12-21
Hello I have just recently installed unbuntu and my wireless seems not to be working, I would like to know can anybody help me with this? I have a Compaq Prestario 1500 laptop and im not too sure how to get wireless working. But my Ethernet works fine but i would love to use that for my xbox XD. 

Thanks,
Dutty

---

### Post by grahammechanical on 2010-12-21
Network manager is designed to use a wired connection first if one is available. If one is not available then it will offer a wireless connection. It is possible to have ethernet and wireless connections at the same time. That is the set up I have at this moment.

When you left click the network icon do you see a list of available wireless connections? when you right click do you see a tick mark against Enable Networking and Enable Wireless? If you go to Edit Connections and select your Wireless Connection is it set to Automatically Connect?

You are using a laptop, so, is wireless switched on in hardware by means of a FN+function key combination? Is wireless switched on in hardware? When Windows shuts down it can switch off the wireless adapter. This is not always switched on when Ubuntu when it boots.

Regards.

---

### Post by duttyg on 2010-12-21
im lost on what u said honestly bro, heres my lspci:

00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

would thank much for help!

---

### Post by duttyg on 2010-12-22
BUMP!
help please?..

---

### Post by grahammechanical on 2010-12-22
I was trying to help you by directing you to menus rather than using terminal commands. I understand the menus. I do not understand fully what the listings from commands prove.

I see from lspc this

> 07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)So, you have an Atheros AR5001 Wireless Network Adapter. But, as useful as that information is I cannot use it to advise you. I admit that I am ignorant of these things.

Is the Wireless adapter working? Is it scanning and detecting wireless networks (including your own one)? A left click on the networking icon would answer those questions. It is also possible to run a command to get the same information. I try to work using menus and dialog boxes because this is the stuff that I am more familiar with.

From the private post that you sent me, the wireless adapter is not detecting wireless networks. This is why I asked about switching wireless on by means of the keyboard. I think that it is best to try the simple fixes first.

The Operating System may not have installed drivers for your Atheros wireless network adapter. Go to System>Administration>Additional Drivers and see if it is possible to get the driver by this means. If you need to use terminal commands to get the driver and if you need to install something called ndiswrapper to load the driver, then I cannot advise you because I am not familiar with doing this.

Here is a link to the trouble shooting guide

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Regards.

---

### Post by duttyg on 2010-12-22
Ohh i sorta understand what you are saying now, I'm sure it installed all the driver but it does not find any networks, also it does not give me the option to enable wireless, i had it enabled once, but as i stated above it found no wireless signals although my network indeed was turned on

sorry for being noob/ new to ubuntu bro.

Thanks, 
Dutty

---

### Post by grahammechanical on 2010-12-22
A right click on the network icon will reveal if there is a tick mark against the line Enable Networking and the line Enable wireless. If the tick mark is absent from Enable Networking, then networking is switched off.  If the tick mark is absent from Enable Wireless then it is wireless that is switched off. It should be possible to select either of these two lines and click on them to provide the tick mark. This should things start working. You may need to reboot.

You can also use a terminal to test this. Type rfkill list and see if it says Soft Blocked:Yes and/or Hard Blocked:Yes. If wireless is Soft Blocked then it is switched off in software. If wireless is Hard Blocked then it is switched off in hardware.

Please understand that you do not need to apologize for being new or for not understanding things. If we demand that you apologize for being new or a learner, then we are not the sort of people we ought to be. I am also new. Not so new as you but almost as new. What we are doing is learning and it does not matter how little we know we can still try to help others. This is why this forum is called a community forum. And you never know, one day I may actually make a suggestion that actually solves someone's problem.

Regards

---

