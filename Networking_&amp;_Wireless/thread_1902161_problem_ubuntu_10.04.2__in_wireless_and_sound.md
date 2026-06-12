---
title: "problem ubuntu 10.04.2  in wireless and sound"
date: 2011-12-30
forum: Networking &amp; Wireless
---

### Post by AymanT on 2011-12-30
hi  i setup ubuntu 10.04.2        
ok    i have problem in wireles and sound not working after setup  i went   update manager  i do update after setup    this  system 
ihave  HP G62  plz      give me these cods 
 
i have question these cods  diffrent between  other kind of  ubuntu and onther   laptops       or dont diffrent

---

### Post by AymanT on 2011-12-30
plz  where is the answer :confused::confused::(:(:(

---

### Post by overdrank on 2011-12-30
Hi and welcome, please do not pm for support.

 I am assuming you mean you are not able to update your system?

---

### Post by AymanT on 2011-12-30
befor and after  update this system   wireless and sound not working       can u give me codes    in terminal for sound and wireless

---

### Post by overdrank on 2011-12-30
> **AymanT said:**
> befor and after  update this system   wireless and sound not working       can u give me codes    in terminal for sound and wireless

Could you post the out put of the command ```
lspci
```

In the terminal to identify your hardware. That is a lower case L in the command. Then we can search for answer that may help.

---

### Post by AymanT on 2011-12-30
aymant@aymant-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
  

this cod no come with me   hhhh

---

### Post by overdrank on 2011-12-30
> **AymanT said:**
> aymant@aymant-laptop:~$ lspci

02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe


this cod no come with me   hhhh

After a quick search of the forums, there are many threads on that model [_RaLink RT3090_]("http://ubuntuforums.org/showthread.php?t=1476007&highlight=RaLink+RT3090+Wireless"). Good luck

---

