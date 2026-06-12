---
title: "Broadcom BCM4331"
date: 2013-08-11
forum: Networking &amp; Wireless
---

### Post by jesus3 on 2013-08-11
Hello, I recently installed linux on my macbook pro through partitioning and almost everything works out of the box except it does not pick up my mouse(track pad works) and I can't to the internet with wireless. I have looked up drivers but I have found nothing useful. 

I know this is a common problem with a simple solution, but I am pretty new to linux so please don't be rude about my lack of knowledge :))))

Thanks

---

### Post by jesus3 on 2013-08-11
My wireless chipset is
```
Broadcom Corporation BCM4331 802.11/a/b/g/n [14e4:4331]
```

---

### Post by ant2 on 2013-08-11
Have you read this: [Ubuntu 12.10 wireless trouble mac book pro]("http://askubuntu.com/questions/248830/ubuntu-12-10-wireless-trouble-macbook-pro")

---

### Post by jesus3 on 2013-08-11
ill try that! thanks a million haha.

I will post my results!

---

### Post by jesus3 on 2013-08-11
I get this:
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-firmware-nonefree

```

---

### Post by wildmanne39 on 2013-08-11
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by ant2 on 2013-08-11
> **jesus3 said:**
> I get this:
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-firmware-nonefree

```

 You did use linux-firmware-nonfree

not

linux-firmware-non**e**free

in the commands?

---

### Post by jesus3 on 2013-08-11
I used non - my bad.

---

### Post by jesus3 on 2013-08-11
I can't copy and paste on this. The trackpad does not work well (only click and move mouse) it won't detect my actual mouse or anything. 

I will do what you said though

---

### Post by jesus3 on 2013-08-11
```
*************** info trace ***************

***** uname -a *****

Linux Jesus 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

***** lspci *****

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4]
    Kernel driver in use: tg3
    Kernel modules: tg3
02:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
    Subsystem: Broadcom Corporation Device [14e4:0000]
    Kernel driver in use: sdhci-pci
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
    Subsystem: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331]
    Kernel driver in use: bcma-pci-bridge

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05ac:8509 Apple, Inc. FaceTime HD Camera
Bus 002 Device 003: ID 0424:2513 Standard Microsystems Corp. 
Bus 002 Device 009: ID 05ac:821d Apple, Inc. 
Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 005: ID 05ac:8242 Apple, Inc. IR Receiver [built-in]
Bus 002 Device 006: ID 05ac:0252 Apple, Inc. Internal Keyboard/Trackpad (ANSI)

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

b43                   378855  0 
mac80211              555198  1 b43
cfg80211              208382  2 b43,mac80211
ssb                    52834  1 b43
bcma                   35762  1 b43

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
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.6
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

filename:       /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     B17695451431A52A474624A
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
vermagic:       3.5.0-23-generic SMP mod_unload modversions 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

filename:       /lib/modules/3.5.0-23-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     657007C65032F6BDD9475AB
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
vermagic:       3.5.0-23-generic SMP mod_unload modversions 

filename:       /lib/modules/3.5.0-23-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     2C92CCB735C6654CB7E788B
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.5.0-23-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

***** dmesg *****

[    8.354410] bcma-pci-bridge 0000:03:00.0: enabling device (0000 -> 0002)
[    8.354448] bcma: Found chip with id 0x4331, rev 0x02 and package 0x09
[    8.354477] bcma: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x25, class 0x0)
[    8.354502] bcma: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1D, class 0x0)
[    8.354559] bcma: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x13, class 0x0)
[    8.418258] bcma: Bus registered
[    9.560627] b43-phy0: Broadcom 4331 WLAN found (core revision 29)
[    9.562873] b43-phy0 ERROR: Firmware file "b43/ucode29_mimo.fw" not found
[    9.562875] b43-phy0 ERROR: Firmware file "b43-open/ucode29_mimo.fw" not found
[    9.562876] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

****************** done ******************

```

---

### Post by wildmanne39 on 2013-08-11
Thre are two drivers this device can use, but I like b43 better.

This should get your wifi working.
```
sudo apt-get install linux-firmware-nonfree
```
Reboot

You need an internet connection to install the firware.
Thanks

---

### Post by jesus3 on 2013-08-11
> **Wild Man said:**
> Thre are two drivers this device can use, but I like b43 better.

This should get your wifi working.
```
sudo apt-get install linux-firmware-nonfree
```
Reboot

You need an internet connection to install the firware.
Thanks

It says that I am unable to locate the package. I have an Internet connection because I posting on this forum on linux. I am using a wired connection of course.

I pasted it in there and it said that..

---

### Post by wildmanne39 on 2013-08-11
From your previous post it says > Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-firmware-non[COLOR="#FF0000"]e[/COLOR]freethe e does not belong there it is non not none.
Thanks

---

### Post by jesus3 on 2013-08-11
> **Wild Man said:**
> From your previous post it says the e does not belong there it is non not none.
Thanks
I copied yours with copy and paste, it I use two fingers it works I guess.

Anyways it still can't find it.

This is what I put in
"sudo apt-get install linux-firmware-nonfree"

---

### Post by 3rdalbum on 2013-08-11
Do:

sudo apt-get update

first.

---

### Post by wildmanne39 on 2013-08-11
Please do:
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
```
Watch for errors while running all commands and if there is any post them here.
Thanks

---

### Post by jesus3 on 2013-08-11
> **3rdalbum said:**
> Do:

sudo apt-get update

first.
Thanks, I did that and then did the apt-get thingy and downloaded and said it unpacked and stop at 
"Setting up linux-firmware-nonfree (1.11ubuntu2) ..." Should I reboot?

---

### Post by wildmanne39 on 2013-08-11
yes

---

### Post by jesus3 on 2013-08-11
> **Wild Man said:**
> yes
Rebooted, one problem still remains, I can't use an external mouse and my trackpad is not really working.

---

### Post by wildmanne39 on 2013-08-11
One issue per thread, if you wireless is solved please use thread tools and mark it solved then start a new thread for your other issue.
Thanks

---

