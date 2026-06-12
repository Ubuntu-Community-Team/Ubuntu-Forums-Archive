---
title: "Acer Aspire One 150, Wireless Failing"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by Mr.Macdonald on 2009-09-13
I just installed the NBR for 9.04 Ubuntu, and am happy with everything but ... the wireless. The card is detected, but the driver doesn't work. iwlist wlan0 scan shows nothing, even though there are 2 wifi networks around.

I have tried several things, and am now going backwards to a fresh installed and update Ubuntu NBR. (Undoing changes)

Please help me fix this, I have a lot of experience with linux so you can speak as such.


Thank You!

---

### Post by sahtepetrucci on 2009-09-13
you can try to build and install madwifi-hal as described in [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

this one worked flawlessly for me until I crashed my system :)

---

### Post by Mr.Macdonald on 2009-09-13
I tried that, and it didn't work!!

Results:
```
aidan@aidan-laptop:~/madwifi-hal-0.10.5.6-r4068-20090705$ lspci -k
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
	Kernel modules: intelfb
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
	Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
	Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
	Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
	Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Kernel modules: iTCO_wdt, intel-rng
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
	Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Kernel modules: i2c-i801
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Kernel driver in use: r8169
	Kernel modules: r8169
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Kernel driver in use: ath_pci
	Kernel modules: ath_pci, ath5k
aidan@aidan-laptop:~/madwifi-hal-0.10.5.6-r4068-20090705$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

aidan@aidan-laptop:~/madwifi-hal-0.10.5.6-r4068-20090705$ iwlist ath0 scan
ath0      No scan results

aidan@aidan-laptop:~/madwifi-hal-0.10.5.6-r4068-20090705$ lsmod | grep ath
ath_rate_sample        20608  1 
ath_pci               221496  0 
wlan                  238320  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               312160  3 ath_rate_sample,ath_pci

```

I will try rebooting!

EDIT:
Still failed, the problem might not be the driver?

---

### Post by sahtepetrucci on 2009-09-14
It seems really strange. Actually the default driver included in Ubuntu 9.04 NBR works in my Acer Aspire One 150, I just tried the madwifi-hal for better performance.

I can mention one of the problems which rarely occurs for me. I use WICD Client (because using LXDE) and it sometimes stops working (maybe one time per month), so I switch to Windows, disable and enable wireless with the switch in the right bottom of the netbook, reboot to Linux and voila, it works.

This problem (which could be solved without any Microsoft product) can be similar to yours, so I advise you to make necessary changes to use your switch and wireless led. Maybe switching off and switch on can help.

Otherwise, you can try to use ndiswrapper with a fresh installation.

This wireless issue is very bizarre about Atheros cards, so I cannot understand exactly what is the problem.

---

### Post by sahtepetrucci on 2009-09-14
One more point: Another user of AAO 150 says that he added acer_wmi module to blacklist.conf in order to use madwifi-hal without any problem.

Did you tried that?

---

