---
title: "Linux Ubuntu 9.10 wireless connection problem. Please help!!?"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by HH8823WP on 2010-01-15
Everything else works fine on Ubuntu 9.10 except when I try to connect to the internet. I have wireless. It just keeps connecting nonstop and never connects. I don't know what to do. Please help me. What should I do? I'm using Acer Aspire 5534 with Windows 7.

---

### Post by bkratz on 2010-01-15
> **HH8823WP said:**
> Everything else works fine on Ubuntu 9.10 except when I try to connect to the internet. I have wireless. It just keeps connecting nonstop and never connects. I don't know what to do. Please help me. What should I do? I'm using Acer Aspire 5534 with Windows 7.

What is really needed is your wireless adapter description
You can get this from the terminal

lspci -nn
that is LSPCI in lowercase) and post the output here or just decode

---

### Post by HH8823WP on 2010-01-15
> **bkratz said:**
> What is really needed is your wireless adapter description
You can get this from the terminal

lspci -nn
that is LSPCI in lowercase) and post the output here or just decode

how do i find this out?

---

### Post by bkratz on 2010-01-15
> **HH8823WP said:**
> how do i find this out?

Go to the terminal at

Applications >> Accessories >>Terminal and type in the command  
lspci -nn. You can copy/paste by highlighting the output and right clicking copy.

---

### Post by herbertportillo on 2010-01-15
Open a Terminal (Applications -> Accessories -> Terminal) and type
```
lspci -nn
``` and copy and paste the results.

---

### Post by HH8823WP on 2010-01-15
Do I do that in windows or ubuntu?

---

### Post by bkratz on 2010-01-15
> **HH8823WP said:**
> Do I do that in windows or ubuntu?

In Ubuntu (it won't exist in Windows)

---

### Post by HH8823WP on 2010-01-15
Oh ok. I gotta re-install Ubuntu from Wubi again. Does it matter what installation size I use?

---

### Post by bkratz on 2010-01-15
> **HH8823WP said:**
> Oh ok. I gotta re-install Ubuntu from Wubi again. Does it matter what installation size I use?

Well I just visited the wubi site (since I have never used Wubi myself) and it specifies at least 5 gig but recommends 8 gig. I suspect any programs you would want to use would exist in this space so i would make it bigger than minimum.

---

### Post by bkratz on 2010-01-15
As I said in the PM windows 7 identifies the wireless device by the number you gave and Ubuntu identifies it as an AR928X see below about the Acer Aspire

[http://ubuntuforums.org/showthread.php?t=1336426](http://ubuntuforums.org/showthread.php?t=1336426)
[http://ubuntuforums.org/showthread.php?t=1311832](http://ubuntuforums.org/showthread.php?t=1311832)
[http://ubuntuforums.org/showthread.php?t=1346392&page=3](http://ubuntuforums.org/showthread.php?t=1346392&page=3)


Threads on getting the AR928X working

[http://ubuntuforums.org/showthread.php?t=1309605&highlight=AR928X](http://ubuntuforums.org/showthread.php?t=1309605&highlight=AR928X)
[http://ubuntuforums.org/showpost.php?p=8599246&postcount=5](http://ubuntuforums.org/showpost.php?p=8599246&postcount=5)

You may have a lot of reading ahead!

---

### Post by HH8823WP on 2010-01-15
Thanks man. Greatly appreciated.

---

### Post by sailthesea on 2010-01-15
I think this should be here 

From OP: HH8823WP
First Cup of Ubuntu
 
Join Date: Jan 2010
Beans: 12
	
My lspci
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) [1022:9602]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3c)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612]
02:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev ff)
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)

---

