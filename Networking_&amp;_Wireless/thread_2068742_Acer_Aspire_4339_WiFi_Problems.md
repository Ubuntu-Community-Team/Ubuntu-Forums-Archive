---
title: "Acer Aspire 4339 WiFi Problems"
date: 2012-10-09
forum: Networking &amp; Wireless
---

### Post by sonofapixel on 2012-10-09
Hello,
I am very new to the Ubuntu Operating System and Linux overall. But I have recently acquired a Acer Aspire 4339-2618 that has Ubuntu Linux 12.04.1 installed as an operating system. This computer happens to have a problem where if you step about 15 feet away from the router you get disconnected from the internet/network. I have attempted to re-install Ubuntu and just change the router completely but that did not work at all. So if anyone can give me some help it would be ***_GREATLY _***appreciated. 

Thank you for your assistance! :)

---

### Post by bra|10n on 2012-10-09
Please post the output using the code tags (#) of 
```
lspci -k
```

---

### Post by sonofapixel on 2012-10-09
Here are the results:
Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
	Subsystem: Acer Incorporated [ALI] Device 0603
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
	Subsystem: Acer Incorporated [ALI] Device 0603
	Kernel driver in use: i915
	Kernel modules: i915
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Acer Incorporated [ALI] Device 0603
	Kernel driver in use: mei
	Kernel modules: mei
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0603
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0603
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0603
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0603
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0603
	Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0603
	Kernel modules: i2c-i801
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0603
	Kernel modules: intel_ips
01:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)
	Subsystem: Acer Incorporated [ALI] Device 0603
	Kernel driver in use: atl1c
	Kernel modules: atl1c
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Foxconn International, Inc. Device e016
	Kernel driver in use: ath9k
	Kernel modules: ath9k
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0603
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0603
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0603
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0603
7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0603
7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0603

---

### Post by Stabadie on 2012-10-09
I have the same issue with the same Acer model, 4339-2618. I've had this notebook for a while now and have never found a fix for the problem. Right after purchasing the notebook I found someone claiming it was possibly a hardware issue or that the wireless module was under-powered. I'm unsure if this is true or not.

If someone can find a fix for this issue, holy hell would I be grateful. This little cheapo notebook has worked great besides this nagging wireless problem.

If there is any info I can give to possibly track down the problem I will be glad to give it.

---

### Post by bra|10n on 2012-10-09
@sonafapixel,

Please post the outputs of,
```
modinfo ath9k
```and 
```
modinfo atl1c
```

---

### Post by sonofapixel on 2012-10-09
RESULTS(ath9k):
filename:       /lib/modules/3.2.0-29-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     01F684AA969715028EA1301
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,cfg80211,ath
intree:         Y
vermagic:       3.2.0-29-generic-pae SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
RESULTS(atl1c)
filename:       /lib/modules/3.2.0-29-generic-pae/kernel/drivers/net/ethernet/atheros/atl1c/atl1c.ko
version:        1.0.1.0-NAPI
license:        GPL
description:    Atheros 1000M Ethernet Network Driver
author:         Jie Yang <jie.yang@atheros.com>
srcversion:     994F608D5E92045E005AAEA
alias:          pci:v00001969d00001083sv*sd*bc*sc*i*
alias:          pci:v00001969d00001073sv*sd*bc*sc*i*
alias:          pci:v00001969d00002062sv*sd*bc*sc*i*
alias:          pci:v00001969d00002060sv*sd*bc*sc*i*
alias:          pci:v00001969d00001062sv*sd*bc*sc*i*
alias:          pci:v00001969d00001063sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-29-generic-pae SMP mod_unload modversions 686

---

### Post by bra|10n on 2012-10-10
Thank you for posting the outputs. I initially thought your hardware was using an alternate driver as possibly none was available for your exact model, but it this respect all seems to be ok. 
Stabadie made reference to the hardware itself possibly being underpowered, which sounds very feasible to me. I can only suggest chasing this up further if the time and effort to each of you is worth it with the relevant developer(s).

---

### Post by sonofapixel on 2012-10-10
I have tried it on Windows with success. But it only doesn't cooperate with Linux.

---

### Post by bra|10n on 2012-10-10
> **sonofapixel said:**
> I have tried it on Windows with success. But it only doesn't cooperate with Linux.

I don't doubt what you say. The failing in Linux is *probably* due to the kernel support and network drivers not being quite up to par for your hardware, therefore not giving you the performance you desire. 

On the up side Google revealed many threads where the hardware vendor and kernel developers working closely to provide a better experience for these cards. 
Please keep in mind also the amount of $ MS throws at these vendors in one way or another to avoid such issues.
As I suggested yesterday you might want to contribute/participate a little closer to the 'action' with this.

Or perhaps someone else here might chime in with some suggestions...
In the end I am sorry I was unable to help.

---

### Post by sonofapixel on 2012-10-10
It is fine. Thank you for your assistance.

---

### Post by Stabadie on 2012-10-11
> **bra|10n said:**
> On the up side Google revealed many threads where the hardware vendor and kernel developers working closely to provide a better experience for these cards. 
Please keep in mind also the amount of $ MS throws at these vendors in one way or another to avoid such issues.
As I suggested yesterday you might want to contribute/participate a little closer to the 'action' with this.

I don't have any Ubuntu dev experience or much knowledge in hardware drivers to be of much help. I'm guessing this is what you meant by contributing closer to the action. Truthfully I'm not even sure where to look to find groups that would be working on this or where to even start to provide help.

Would you mind pointing me to a community that may be welcoming to someone with only small bits of knowledge in this topic?

---

### Post by wildmanne39 on 2012-10-11
Hi, please try:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Thanks

---

### Post by Stabadie on 2012-10-13
From quick testing, that appears to have done the trick. Thanks! Now I can walk to the other side of the house and still keep a wireless connection. I'll do further testing to be sure, but it definitely appears to be better.

If you wouldn't mind answering for future reference, what exactly did those commands do?

---

### Post by wildmanne39 on 2012-10-13
Hi, it changes encryption from hardware to software and with this wireless card it usually helps a lot.
Thanks

---

