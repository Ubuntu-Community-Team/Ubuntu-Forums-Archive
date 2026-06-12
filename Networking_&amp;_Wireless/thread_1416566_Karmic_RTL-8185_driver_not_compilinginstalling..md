---
title: "Karmic: RTL-8185 driver not compiling/installing."
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by taurolyon on 2010-02-26
I downloaded the RealTek 8185 drivers from the RealTek site. I was following the instructions in the README file, however I get errors when attempting to compile them.

> jay@Jay-desktop:~/Downloads/rtl8185_linux_26.1031.1207.2009.release$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
  CC [M]  /home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.o
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c: In function ‘proc_get_stats_hw’:
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c:350: warning: cast from pointer to integer of different size
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c:351: warning: cast from pointer to integer of different size
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c:354: warning: cast from pointer to integer of different size
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c:355: warning: cast from pointer to integer of different size
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c:358: warning: cast from pointer to integer of different size
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c:359: warning: cast from pointer to integer of different size
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c: In function ‘check_tx_ring’:
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c:826: warning: cast from pointer to integer of different size
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c:826: warning: cast from pointer to integer of different size
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c:827: warning: cast from pointer to integer of different size
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c:827: warning: cast from pointer to integer of different size
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c: In function ‘alloc_tx_desc_ring’:
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c:1447: warning: cast from pointer to integer of different size
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c:1447: warning: cast to pointer from integer of different size
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c: In function ‘alloc_rx_desc_ring’:
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c:1621: warning: cast from pointer to integer of different size
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c:1621: warning: cast to pointer from integer of different size
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c: In function ‘rtl8180_rx’:
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c:2065: error: implicit declaration of function ‘rdtsc_rtl’
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c: In function ‘rtl8180_watch_dog’:
/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c:2793: warning: unused variable ‘bEnterPS’
make[2]: *** [/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.o] Error 1
make[1]: *** [_module_/home/jay/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'
make: *** [all] Error 2


Am I missing some complier component?

---

### Post by taurolyon on 2010-02-26
And I did attempt a "$ sudo make" attempt to see if it was a permission problem.

---

### Post by taurolyon on 2010-02-26
I even tried ndiswrapper and the x64 driver from the realtek site, unfortunatly, no go... 

Any help would be appreciated, as I'm at a loss here...

---

### Post by chili555 on 2010-02-26
I wonder if the built-in rtl8180.ko is appropriate for your card, saving us all from compiling. Please post:```
lspci -nn
```Thanks.

---

### Post by GeoMX on 2010-06-11
How did you solve it?

---

### Post by Pithikos on 2010-06-29
Same problem here :/ I have been figting with this for 2 days now without much success. [COLOR=Red]lspci -nn [COLOR=Black]gives me:[/COLOR][/COLOR]```
00:00.0 RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [10de:03ea] (rev a1)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP61 LPC Bridge [10de:03e0] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP61 SMBus [10de:03eb] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [10de:03f5] (rev a2)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP61 SMU [10de:03f4] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f1] (rev a3)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f2] (rev a3)
00:04.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI bridge [10de:03f3] (rev a1)
00:05.0 Audio device [0403]: nVidia Corporation MCP61 High Definition Audio [10de:03f0] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP61 IDE [10de:03ec] (rev a2)
00:08.0 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:08.1 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:09.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e8] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:0d.0 VGA compatible controller [0300]: nVidia Corporation C61 [GeForce 6150SE nForce 430] [10de:03d0] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control [1022:1204]
01:09.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 46)
01:0a.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)

```[COLOR=Red]

[COLOR=Black]I run Ubuntu 10.04 x64.[/COLOR]
[/COLOR]

---

### Post by GeoMX on 2010-06-29
I don't know why the post is marked as solved but no solution is posted.

This post is about problems compiling the Realtek driver, not about the card not working ;).

I had some issues with an Encore card, but my problem was the motherboard :confused:: [http://mextronics.netii.net/en/2010/06/how-to-make-a-rtl-8185-wifi-card-work-with-ubuntu/](http://mextronics.netii.net/en/2010/06/how-to-make-a-rtl-8185-wifi-card-work-with-ubuntu/)

Anyway, I didn't have problems compiling the driver from Realtek.

---

### Post by Pithikos on 2010-06-29
Well I solved my problem with compilation and installing. I have a realtek 8185 card and tryied everything, rtl8180, ndiswrapper. I tryied with the realtek driver but wasn't able to compile/install as it was giving me the same errors as the poster of the thread. What I did was following the instructions given here: [http://ubuntuforums.org/showthread.php?p=9526548](http://ubuntuforums.org/showthread.php?p=9526548)
I managed to compile/install in that way but still was experiencing problems. I ran
```
cp /etc/modprobe.d/ndiswrapper ~ && sudo rm /etc/modprobe.d/ndiswrapper
```to clean all the garbage from ndiswrapper(I had already blacklisted ndiswrapper and rtl8180 but still was experiencing problems). After that everything worked for me.
So the solution to your problem is the link mentioned ;)

---

