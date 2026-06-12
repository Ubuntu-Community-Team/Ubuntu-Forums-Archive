---
title: "Wireless not detected on hp Compaq 6735s ubuntu 10.04"
date: 2013-07-17
forum: Networking &amp; Wireless
---

### Post by Alita99 on 2013-07-17
Hi everybody!

I hope someone could help me! thank you!

Since I installed ubuntu 10.04 in my netbook, wireless network doesn't work.
This is terminal response to lspci command

ahimsa3@ahimsa3-laptop:~$ lspci 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4357 (rev 10)

I heve looked on some forum and on internet, but I don't find how to activate the Network Wireless Interface. Not yet.

So, could anybody help me to find a solution? I also bought a wifi usb adapter (Netgear N300 WNA3100M) but I'm not able to install it! :(

Thank you for help me!

---

### Post by varunendra on 2013-07-17
Please follow the "Wireless Script" link in my signature to download "wireless_script". Run it while the usb one is also plugged in. Post back the result as mentioned in the linked post.

We may try to troubleshoot whichever seems easier.

---

### Post by mörgæs on 2013-07-17
Please don't post the same question twice. I have deleted your other post. 

10.04 is out of support. Better to begin with a fresh install of 13.04.

---

### Post by Alita99 on 2013-07-17
thank you, varunendra
here the wireless info
```


*************** info trace ***************


***** uname -a *****


Linux ahimsa3-laptop 2.6.32-47-generic #109-Ubuntu SMP Tue May 7 02:03:05 UTC 2013 i686 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.4 LTS
Release:	10.04
Codename:	lucid


***** lspci *****


02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:4357] (rev 10)
	Kernel driver in use: sky2
	Kernel modules: sky2


***** lsusb *****


Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 0846:9021 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** iwconfig *****




***** rfkill *****




***** lsmod *****




***** nm-tool *****


NetworkManager Tool


State: connected


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.59
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1






***** NetworkManager.state *****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false


***** NetworkManager.conf *****


nm-system-settings.conf (used up to 10.04):


[main]
plugins=ifupdown,keyfile


[ifupdown]
managed=false




***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****




***** resolv.conf *****


nameserver 192.168.1.1


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


[/etc/modprobe.d/blacklist-local.conf]
blacklist fglrx


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


***** dmesg *****


[   15.390584] platform radeon_cp.0: firmware: requesting radeon/RS780_pfp.bin
[   15.422912] platform radeon_cp.0: firmware: requesting radeon/RS780_me.bin
[   15.427913] platform radeon_cp.0: firmware: requesting radeon/R600_rlc.bin
[ 5504.593674] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[ 5965.024345] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[ 7773.742637] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[ 7774.108671] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
[ 7774.112291] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[ 7774.112300] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[ 7774.112314] ndiswrapper (mp_halt:254): device e28683a0 is not initialized - not halting
[ 7774.112319] ndiswrapper: device eth%d removed
[ 7774.112478] ndiswrapper: probe of 1-5:1.0 failed with error -22


****************** done ******************



```

---

### Post by varunendra on 2013-07-17
> **Alita99 said:**
> ```

Bus 001 Device 006: ID **0846:9021** NetGear, Inc. 
```

The above one is the only wireless adapter the script could detect. It seems your netbook either doesn't have an internal card or is somehow physically disabled/disconnected. You may try resetting the BIOS to see if it can magically make it appear.

Anyway, the above netgear adapter is supported by the native rtl8192cu driver in 12.04 and so you shouldn't need ndiswrapper. But like mörgæs mentioned above, 10.04 desktop is no more supported and so you should upgrade to 12.04 LTS or 13.04. The LTS will be supported till April 2017, while 13.04 only till January next year (but will have newer drivers).

Just download these, run in live mode and install whichever you like more. Most probably, your usb adapter will work out-of-box with both of these. If not, troubleshooting a supported version makes more sense. :)

---

### Post by Alita99 on 2013-07-17
thank you, [COLOR=#000000]varunendra and [/COLOR][COLOR=#000000]mörgæs!
[/COLOR]Now I will search some help to install 12.04 LTS!

---

### Post by varunendra on 2013-07-17
> **Alita99 said:**
> Now I will search some help to install 12.04 LTS!

How to install 12.04 LTS (all the steps will be same for 13.04 also) : [http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin)

Shorter Official guide : [http://www.ubuntu.com/download/desktop/install-desktop-long-term-support](http://www.ubuntu.com/download/desktop/install-desktop-long-term-support)

I recommend using torrents to download the ISO. They are usually faster and ensure integrity of the downloaded data.

Official source for torrents : [http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

Best of Luck !

---

