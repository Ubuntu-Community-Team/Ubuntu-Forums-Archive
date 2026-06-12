---
title: "Cannot open /dev/modem"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by Sakyla on 2009-03-24
In Gnome ppp I get the following error
WvDial<Err>: Cannot open/dev/modem: No such file or directory

This came up after I had done some upgrades and now I cannot get Ubuntu connected to the internet. I don't know which ones upgraded.  Vista does not have a problem.

My system is a dual boot Ubuntu 7.10 and Vista operating on a Dell.

I have tried installing many new drivers as Vista sees the modem as Conexant D850 56K V.90 DFVc Modem.  Ubuntu sees the modem as Conexant HSF 56K Data/fax modem.  

Running scanmodem it wants the driver hsfmodem 7.80.02.02full k2.6.22 16 generic ubuntu i386.deb.zip  Then on the Linuxant website for the Conexant drivers it lists this driver but the actual download name is for a different kernal.  Anyways I tried all of the configurations that I can think of and I still get the same response.

With 
sudo wvdial /etc/wvdial.conf
the response is
warning:section [Dialer /etc/wvdial.conf] does not exist in wvdial.conf
This is with the driver that scanmodem says it needs.

Any help is appreciated as I am getting very frustrated with this process and trying to figure it out for the past 3 weeks.

---

### Post by Sakyla on 2009-03-26
In trying to search out the problem further lspci returned

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1) 
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2) 
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2) 
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2) 
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) 
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) 
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) 
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2) 
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) 
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2) 
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) 
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) 
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem 
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8300 GS (rev a1) 

Can someone tell me if there is a reason here why I can't get Ubuntu to connect to the internet.  Or something else that might provide more info.
Thanks

---

