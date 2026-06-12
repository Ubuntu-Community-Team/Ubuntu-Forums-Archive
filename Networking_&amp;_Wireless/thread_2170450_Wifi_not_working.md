---
title: "Wifi not working"
date: 2013-08-26
forum: Networking &amp; Wireless
---

### Post by Barry_Dunnage on 2013-08-26
Hi 
I had a working dule boot system with windows 7 and Ubuntu 8. I then installed Ubuntu 13.4 and the wifi will not work this is on a dell studio laptop. When I rremoved ubuntu wifi is working agin on windows 7. Is there any thing I can do or do I have to stay on the old ubuntu.

---

### Post by newb85 on 2013-08-26
Details of your card would be helpful.   Run
```
 sudo lshw -C network 
```
And post the result (in code tags, please).

---

### Post by Barry_Dunnage on 2013-08-26
New hope this gets to you Broardcom BCM 4312

---

### Post by grahammechanical on 2013-08-26
You can see if there is a driver for your wireless adapter. In 13.04 Go to System Settings. You will find it in the Power/cog menu and open Software and Updates and then the Additional Drivers tab. Allow it a little time to search for driver and see if you are offered a driver for your wireless adapter. This is where we also activate video adapters.

There are some checks you can make to confirm a few things.

Do you have a Network Manager icon in the top panel? If you are connected by ethernet it will look like two arrows going in opposite directions. Is there a tick mark against Enable Wi-Fi? Do you see a list of available Wi-Fi networks.

The last time you shutdown in Windows was Wi-Fi working? If the wireless adpater is switched off in Windows then it is unlikely that it will be working in Ubuntu when we load Ubuntu.

Run
```
rfkill list
```

On my system I see

> 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

My Wi-Fi is working. If you see "yes" in one or other place then something is stopping the wirless adapter from working. If it is soft blocked then it is usually the need for a driver. If it is hard blocked then you need to turn the adpater on by pressing a key combination.

Regards

---

### Post by wildmanne39 on 2013-08-26
*Thread moved to **Networking & Wireless**.*

---

### Post by wildmanne39 on 2013-08-26
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by Barry_Dunnage on 2013-08-26
--2013-08-26 19:05:42--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... 54.243.182.80
Connecting to dl.dropbox.com (dl.dropbox.com)|54.243.182.80|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script) [following]
--2013-08-26 19:05:43--  [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script)
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 54.235.141.98
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|54.235.141.98|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4098 (4.0K) [text/plain]
Saving to: `wireless_script'

100%[======================================>] 4,098       --.-K/s   in 0.003s  

Last-modified header missing -- time-stamps turned off.
2013-08-26 19:05:43 (1.48 MB/s) - `wireless_script' saved [4098/4098]


Results saved in "wireless-info.txt".

---

### Post by wildmanne39 on 2013-08-26
Please read the directions in my previous post for attaching the wireless-info.txt that is in your home folder.
Thanks

---

### Post by Barry_Dunnage on 2013-08-27
hi sorry misunderstood
```
*************** info trace ***************

***** uname -a *****

Linux barry-Studio-1737 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 15:31:16 UTC 2013 i686 i686 i386 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: b43-pci-bridge
--
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
    Subsystem: Dell Device [1028:02a0]
    Kernel driver in use: tg3

***** lsusb *****

Bus 001 Device 002: ID 0c45:63fb Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****


***** lsmod *****

b43                   364596  0 
mac80211              541819  1 b43
cfg80211              453853  2 b43,mac80211
bcma                   39810  1 b43
ssb                    51554  1 b43

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
    Address:         192.168.1.181
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

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****

nameserver 127.0.0.1
search default

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

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/b43/b43.ko
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
vermagic:       3.8.0-29-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/bcma/bcma.ko
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
vermagic:       3.8.0-29-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/ssb/ssb.ko
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
vermagic:       3.8.0-29-generic SMP mod_unload modversions 686 


***** udev rules *****

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.5/0000:08:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

***** dmesg *****

[    1.452493] ssb: Found chip with id 0x4312, rev 0x01 and package 0x00
[    1.452514] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    1.452531] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    1.452550] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    1.452567] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    1.516332] ssb: Sonics Silicon Backplane found on PCI device 0000:04:00.0
[    9.649197] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[    9.692237] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[    9.730127] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[    9.730194] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[    9.730242] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

****************** done ******************
```

---

### Post by wildmanne39 on 2013-08-27
Please do:
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
sudo modprobe -r b43
sudo modprobe b43
```
watch for errors.
Thanks

---

### Post by Barry_Dunnage on 2013-08-29
That's fixed it thanks for all your help

---

### Post by cbhr2 on 2013-08-29
Hi, I have a notebook hp mini 1000 and it installed all the drivers successfully but the wifi light does not change


AcAV try this code sudo modprobe b43 and if the light changes to blue wifi but when I restart the notebook returns to Orange

---

### Post by wildmanne39 on 2013-08-29
Do:
```
sudo su 
echo b43 >> /etc/modules 
exit
```
Thanks

---

### Post by cbhr2 on 2013-08-29
thank you for finally solved!

---

