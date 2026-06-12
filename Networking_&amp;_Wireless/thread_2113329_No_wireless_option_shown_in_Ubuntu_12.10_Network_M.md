---
title: "No wireless option shown in Ubuntu 12.10 Network Manager - Acer AO756"
date: 2013-02-07
forum: Networking &amp; Wireless
---

### Post by christina1990 on 2013-02-07
Hi everyone,

I recently bought an Acer Aspire One 756 and installed Ubuntu 12.10. Things have been working fine and I have no problem using the wired connection at home. However, the network manager does not give me the option to "Enable Wireless" as it did on my previous notebook. There is only the option to "Enable Networking".  No wireless connections are shown. 

If I enter the "Edit Connections..." dialogue and open the "Wireless" tab, I am given the option to add a wireless connection manually. I don't know if that would work since I don't know about the information I'm prompted to enter. 

Please let me know about any commands I can run to gather more information about the problem. Thank you in advance!

Christina

---

### Post by christina1990 on 2013-02-07
Update: I ran lspci. Do you guys think that there's any interesting information here?

```
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0106] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
00:1c.2 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 [8086:1e14] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation 7 Series Chipset Family LPC Controller [8086:1e5e] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
04:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
04:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
```How can I figure out which network adapter I have and whether the correct drivers are installed?

---

### Post by christina1990 on 2013-02-07
Update: Wirless inexplicably started working after I ran the following commands:

```
sudo apt-get install linux linux-headers-generic kernel-package

sudo apt-get install --reinstall bcmwl* firmware-b43-lpphy-installer b43-fwcutter
```I found this fix on 

[http://www.upubuntu.com/2012/10/how-to-fix-unity-and-wireless-problems.html](http://www.upubuntu.com/2012/10/how-to-fix-unity-and-wireless-problems.html)

---

