---
title: "Wireless BCM4312 LP-PHY can not connect on 13.04"
date: 2013-06-09
forum: Networking &amp; Wireless
---

### Post by leg on 2013-06-09
I upgraded to 13.04 last week and I have been unable to connect through my wireless conneciton since. I have followed your instructions for building a replacement driver and I still have the same problems. I have run your script and here is the output:

wireless-info.txt
```

*************** info trace ***************

***** uname -a *****

Linux lg-Inspiron-1750 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring

***** lspci *****

09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
	Subsystem: Dell Device [1028:0406]
	Kernel driver in use: sky2
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
	Kernel driver in use: b43-pci-bridge

***** lsusb *****

Bus 001 Device 003: ID 05ca:180c Ricoh Co., Ltd 
Bus 002 Device 002: ID 05dc:a768 Lexar Media, Inc. 
Bus 007 Device 002: ID 062a:0252 Creative Labs Emerge Uni-retractable Laser Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** iwconfig *****


***** rfkill *****


***** lsmod *****

b43                   378642  0 
bcma                   41051  1 b43
mac80211              606457  1 b43
cfg80211              510937  2 b43,mac80211
ssb                    56748  1 b43

***** nm-tool *****

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****


***** resolv.conf *****


***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** dmesg *****

[    0.976341] ssb: Found chip with id 0x4312, rev 0x01 and package 0x00
[    0.976362] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    0.976380] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    0.976397] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    0.976414] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    1.048585] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[   15.235141] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   15.276896] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   15.402199] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   15.402200] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   15.402202] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

****************** done ******************

```

and the output of modinfo wl
```
filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/wl.ko
srcversion:     49E2D90EE4D6877632DEDB0
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000435Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A99Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
depends:        lib80211
vermagic:       3.8.0-19-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           name:string
```

I have noticed that my driver seems to be blacklisted (b43) and have commented that line but this has not worked either. I am currently using a live usb stick with Ubuntu 13.04 on it and wireless works fine while usinf this. If I reboot into my installed version (installed using this flash drive) the wireless will not work. There is no option to select it from top menu bar and there is no entry in the system settings -> network section either.

When booting my installed version I notice error messages around PHY0 which you can see in the dmesg section of your output.

I did also have problems in 12.04 with this driver and fixed it that time through this[ thread]("http://ubuntuforums.org/showthread.php?t=2086166"). I have tried this fix again but not with the current installation.

---

### Post by Hadaka on 2013-06-09
@leg

Hi, the patch you applied is for the wl driver and this card...
```
Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727]
```

your card is not the same and requires a different driver..
```
Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315]<-your card
```

Please open a terminal and do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt get install firmware-b43-lpphy-installer
sudo modprobe b43
```
*If this does NOT fix your problem, please start a new thread
as your card is not the same.
thanks.

---

### Post by leg on 2013-06-10
ok I can see that now but the problem I have is that I have no network without my wireless. How can I achieve this by downloading the driver I need using the live usb disk and then applying it from my install.

---

### Post by varunendra on 2013-06-10
> **leg said:**
> ok I can see that now but the problem I have is that I have no network without my wireless. How can I achieve this by downloading the driver I need using the live usb disk and then applying it from my install.

Download the "linux-firmware-nonfree" package from here : [http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download)

Copy it to your Ubuntu machine and double-click to install. Then remove the incorrect packages if you haven't already -
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Reboot and see if your wireless starts working.

---

### Post by leg on 2013-06-10
Thank you will attempt that tonight and let you know.

---

### Post by s.fox on 2013-06-10
Posts moved into own thread :)

---

### Post by leg on 2013-06-10
> **varunendra said:**
> Download the "linux-firmware-nonfree" package from here : [http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download)

Copy it to your Ubuntu machine and double-click to install. Then remove the incorrect packages if you haven't already -
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Reboot and see if your wireless starts working.

Thank you very much I am now on line from my installation wireless working nicely. I apologise for the schoolboy error or trying to install the wrong driver.

---

### Post by varunendra on 2013-06-10
> **leg said:**
> Thank you very much I am now on line from my installation wireless working nicely. I apologise for the schoolboy error or trying to install the wrong driver.
No problem! And that driver confuses even many of the well experienced users, especially since it is suggested by the OS itself. :P

Perhaps some of us need to become developers as well and see why it does so.. :-k (and of course fix it thereafter).

---

