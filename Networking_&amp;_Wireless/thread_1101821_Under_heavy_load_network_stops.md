---
title: "Under heavy load network stops"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by wmatthews on 2009-03-20
I have my home server that routes the internet for me with wireless.

My first set up was "Ethernet controller: D-Link System Inc DL2000-based Gigabit Ethernet (rev 0c)" connected to the network, 'Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)" connected to the DSL and Ethernet controller: Atheros Communications Inc. "Atheros AR5001X+ Wireless Network Adapter (rev 01)" connected for the wireless.

The problem is that the "Ethernet controller: D-Link System Inc DL2000-based Gigabit Ethernet (rev 0c)" will disconnect when ever it is a heavy load from the wired network.  So I thought a simple solution would be to switch the LAN and DSL connections because the DSL connection is on 10 megs a second instead of having it hooked up at 100 megs a second on the network.  This did not work.  

I am using it now for to post here but if I get on another computer and start transferring some from the internet it is going to stop. I will have to restart the computer to get it to work again.  "/etc/init.d/networking restart" does nothing to help, neither does "ifdown eth1" "ifup eth1".

I did a lot of searching on the net for a solutions and came up with the dl2k driver for the card but I can't get it built.  I don't know what it is using now.  If someone can help me figure out that it would be helpful also.


Here is my lspci:

```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
03:09.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
03:0a.0 Ethernet controller: D-Link System Inc DL2000-based Gigabit Ethernet (rev 0c)
```

p.s.
There is no information in "dmesg" nor "/var/log/messages" about the card taking a dive when it happens.

---

### Post by wmatthews on 2009-03-20
Bump, I know someone can help me out.

---

### Post by weather15 on 2009-03-20
That's and idea to try. I am also having a problem with my wireless adapter it seems when I connect to a wireless network that uses WPA Personal Authentication the connection seems to drop at random.

---

### Post by wmatthews on 2009-03-20
I was having that problem on 8.10.  I don't have it with 9.04 beta 1.

---

### Post by wmatthews on 2009-03-20
Bump, come on folks I need help.  Someone just jumped on one of my other computers and I had to shut her down again.  ANY help is greatly appreciated.

---

### Post by wmatthews on 2009-03-21
For a second I thought that upgrading the kernel didn't work. I had to learn how to make the kernel use the module that I needed for the card.

After 2 1/2 long days it is finally working.

There is a module called dl2k that is included in kernels that need to be enabled. You can also download the module from [Sourceforge]("http://dl2k.sourceforge.net/"). I didn't have any luck compiling it so I suggest just learning how to compile a kernel. It isn't hard at all.

I haven't figured out how to blacklist the ipp module that was being used but that can wait until tomorrow.

---

