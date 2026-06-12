---
title: "Trouble getting my WiFi to work in 8.10"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by jeffchase on 2009-06-24
Here is my response from lspci -nn
lshw - Network
dmesg | grep - e ath -e wlan
uname -rm
I would appreciate any help that you could give me.

jeff@jeff-laptop:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation Unknown device [10de:0754] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation Unknown device [10de:075e] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation Unknown device [10de:0752] (rev a1)
00:01.3 Co-processor [0b40]: nVidia Corporation Unknown device [10de:0753] (rev a2)
00:01.4 RAM memory [0500]: nVidia Corporation Unknown device [10de:0568] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation Unknown device [10de:077b] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corporation Unknown device [10de:077c] (rev a1)
00:04.0 USB Controller [0c03]: nVidia Corporation Unknown device [10de:077d] (rev a1)
00:04.1 USB Controller [0c03]: nVidia Corporation Unknown device [10de:077e] (rev a1)
00:06.0 IDE interface [0101]: nVidia Corporation Unknown device [10de:0759] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation Unknown device [10de:0774] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:075a] (rev a1)
00:09.0 IDE interface [0101]: nVidia Corporation Unknown device [10de:0ad0] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation Unknown device [10de:0760] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:0569] (rev a1)
00:14.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:077a] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control [1022:1303]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Link Control [1022:1304]
02:00.0 VGA compatible controller [0300]: nVidia Corporation Unknown device [10de:0845] (rev a2)
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
jeff@jeff-laptop:~$ lswh -c Network
bash: lswh: command not found
jeff@jeff-laptop:~$ lshw -c Network
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

    -version        print program version (B.02.12.01)

format can be
    -html           output hardware tree as HTML
    -xml            output hardware tree as XML
    -short          output hardware paths
    -businfo        output bus information

options can be
    -class CLASS    only show a certain class of hardware
    -C CLASS        same as '-class CLASS'
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
    -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
    -quiet          don't display status
    -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

jeff@jeff-laptop:~$ dmesg | grep -e ath -e wlan
[   34.095401] ath_hal: module license 'Proprietary' taints kernel.
[   34.130474] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   33.748030] wlan: 0.9.4
[   33.798566] ath_pci: 0.9.4
jeff@jeff-laptop:~$ uname -rm
2.6.24-19-generic i686
jeff@jeff-laptop:~$

---

### Post by philcamlin on 2009-06-24
why dont you go to 9.04 

most people are using it and would have more of an idea of whats wrong

:popcorn:

---

### Post by Milfus_Azorica on 2009-06-24
Same problem here. I believe it was because the last sistem update. Maybe if we can do a sistem update!!?? but i dont know how.

 im noob with ubuntu so if anyone could help i apreciate too!

My 8.10 was almost perfect...almost zero windows use until this problem hapened.

I can see my wireless network but all software cant conect to the internet.

---

### Post by philcamlin on 2009-06-24
upgrade to 9.04 it has more driver support 

its like trying to find drivers for a windows 95 when vista is out :popcorn:

---

### Post by jeffchase on 2009-06-24
I would love to upgrade, but I fear that if I upgrade with all of the issues that I am having, that some problems won't be resolved. Any advice in that regard?

---

