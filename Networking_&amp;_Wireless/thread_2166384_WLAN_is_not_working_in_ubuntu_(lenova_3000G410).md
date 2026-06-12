---
title: "WLAN is not working in ubuntu (lenova 3000G410)"
date: 2013-08-09
forum: Networking &amp; Wireless
---

### Post by thannara123 on 2013-08-09
Hello experts iam new to here . I installed ubunt 13.04 and windows xp .
in xp WLAN working perfectly . 
but in ubuntu it is not working .
please help me 
advance thanks

---

### Post by lukeiamyourfather on 2013-08-09
Try opening the hardware drivers utility in Ubuntu. Sometimes there are proprietary drivers available. If there's nothing there you might need to install drivers manually from the manufacturer (if they exist).

---

### Post by thannara123 on 2013-08-10
Anybody help me

---

### Post by praseodym on 2013-08-10
Please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
iwconfig
lsmod
rfkill list
```

---

### Post by thannara123 on 2013-08-10
Sir pleas see the result 
[https://plus.google.com/photos/110033695214700618956/albums/5910690530992952529/5910690552647330258?pid=5910690552647330258&oid=110033695214700618956](https://plus.google.com/photos/110033695214700618956/albums/5910690530992952529/5910690552647330258?pid=5910690552647330258&oid=110033695214700618956)

[https://plus.google.com/photos/110033695214700618956/albums/5910690530992952529/5910690532823401650?pid=5910690532823401650&oid=110033695214700618956](https://plus.google.com/photos/110033695214700618956/albums/5910690530992952529/5910690532823401650?pid=5910690532823401650&oid=110033695214700618956)

[https://plus.google.com/photos/110033695214700618956/albums/5910690530992952529/5910690535731648258?pid=5910690535731648258&oid=110033695214700618956](https://plus.google.com/photos/110033695214700618956/albums/5910690530992952529/5910690535731648258?pid=5910690535731648258&oid=110033695214700618956)

[https://plus.google.com/photos/110033695214700618956/albums/5910690530992952529/5910690540357598850?pid=5910690540357598850&oid=110033695214700618956](https://plus.google.com/photos/110033695214700618956/albums/5910690530992952529/5910690540357598850?pid=5910690540357598850&oid=110033695214700618956)

[https://plus.google.com/photos/110033695214700618956/albums/5910690530992952529/5910690549208029714?pid=5910690549208029714&oid=110033695214700618956](https://plus.google.com/photos/110033695214700618956/albums/5910690530992952529/5910690549208029714?pid=5910690549208029714&oid=110033695214700618956)

---

### Post by thannara123 on 2013-08-11
no one here ?

---

### Post by praseodym on 2013-08-11
C/P the outputs into a text file

---

### Post by varunendra on 2013-08-11
Or even better, follow the "Wireless Script" link in my signature > follow the instructions in the linked post to download and run the script > post back the "wireless-info.txt" file it creates.

---

### Post by thannara123 on 2013-08-11
Wireless -info-txt as follws .thanks in advance 

```
*************** info trace ***************

***** uname -a *****

Linux gelectron-laptop 3.8.0-27-generic #40-Ubuntu SMP Tue Jul 9 00:19:35 UTC 2013 i686 i686 i686 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

***** lspci *****

04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0465]
    Kernel driver in use: b43-pci-bridge
06:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
    Subsystem: Lenovo Device [17aa:3861]
    Kernel driver in use: tg3

***** lsusb *****

Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

***** lsmod *****

b43                   351961  0 
bcma                   39645  1 b43
mac80211              526519  1 b43
cfg80211              436177  2 b43,mac80211
ssb_hcd                12749  0 
ssb                    50834  2 b43,ssb_hcd

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



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

nameserver 127.0.1.1
search Home

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

***** modinfo *****

filename:       /lib/modules/3.8.0-27-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     F6F97440A9DA6418F4C2856
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,mac80211,bcma,cfg80211
intree:         Y
vermagic:       3.8.0-27-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

filename:       /lib/modules/3.8.0-27-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F7A1658A8CB1D58E3D347C1
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.8.0-27-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.8.0-27-generic/kernel/drivers/usb/host/ssb-hcd.ko
license:        GPL
description:    Common USB driver for SSB Bus
author:         Hauke Mehrtens
srcversion:     E127A51EDC8F44D2C2A8F15
alias:          ssb:v4243id0819rev*
alias:          ssb:v4243id0817rev*
alias:          ssb:v4243id0808rev*
depends:        ssb
intree:         Y
vermagic:       3.8.0-27-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.8.0-27-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     14621F6EC014F731244437C
alias:          pci:v000014E4d00004350sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D6sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004322sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.8.0-27-generic SMP mod_unload modversions 686 


***** udev rules *****

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.3/0000:06:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

***** dmesg *****

[    1.488114] ssb: Found chip with id 0x4311, rev 0x01 and package 0x00
[    1.488132] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[    1.488142] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[    1.488151] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[    1.488160] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[    1.552276] ssb: Sonics Silicon Backplane found on PCI device 0000:04:00.0
[   10.503263] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   10.549826] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   10.595778] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   10.595840] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   10.595901] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

****************** done ******************
```

---

### Post by thannara123 on 2013-08-11
Thanks its working .....
thanks again

---

### Post by varunendra on 2013-08-12
> **thannara123 said:**
> Thanks its working .....
Really ?? It shouldn't unless you have installed the correct firmware for the driver. So I think by "its working.." you mean the script is working, not the wireless connection. From your output -

```
[   10.595778] b43-phy0 ERROR: **[COLOR="#FF0000"]Firmware file "b43/ucode5.fw" not found[/COLOR]**
[   10.595840] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   10.595901] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/...devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```

The above error message means you need to install the firmware for the wireless driver b43. If you haven't already done that, install it as follows (make sure you are connected to internet via cable while doing this) -
```
sudo apt-get install linux-firmware-nonfree
```
Let the above command finish its job, then reboot or manually reload the driver -
```
sudo modprobe -rfv b43
sudo modprobe -v b43
```

---

