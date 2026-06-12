---
title: "need WIFI help! Broadcom 4301"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by petermg on 2010-05-27
```
petermg@kids-ubuntu:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.

usb0      no wireless extensions.

```

```
petermg@kids-ubuntu:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
```

```
petermg@kids-ubuntu:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
```

```
petermg@kids-ubuntu:~$ iwlist wlan0 scan
wlan0     Failed to read scan data : Network is down

```

```
petermg@kids-ubuntu:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
	device (14E4:4301) present (alternate driver: ssb)
```

```
petermg@kids-ubuntu:~$ dmesg |grep Broad
[   32.412946] b43legacy-phy0: Broadcom 4301 WLAN found
[   32.578941] Broadcom 43xx-legacy driver loaded [ Features: PLID, Firmware-ID: FW10 ]
```

```
petermg@kids-ubuntu:~$ lspci |grep Broad
02:05.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
```

Please help, I don't know what I'm doing wrong, don't know what I could be missing...?! This is on Lucid.

---

### Post by TheGnomeOfMetal on 2010-05-27
use sudo lshw -C network and see if the driver is loaded.

---

### Post by purelinuxuser on 2010-05-27
Try plugging into an Ethernet port and installing the package b43-fwcutter from Synaptic (**during the installation you will get a prompt with a checkbox that says, "Automatically download and install firmware?" be sure it is _CHECKED_**).  Then reboot.

Hope this helps! :)

Edit: Darn, TheGnomeOfMetal beat me to it!

---

### Post by petermg on 2010-05-27
```
petermg@kids-ubuntu:~$ lshw -C
Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.14)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
	-numeric        output numeric IDs (for PCI, USB, etc.)


```

???

---

### Post by petermg on 2010-05-27
> **purelinuxuser said:**
> Try plugging into an Ethernet port and installing the package b43-fwcutter from Synaptic (**during the installation you will get a prompt with a checkbox that says, "Automatically download and install firmware?" be sure it is _CHECKED_**).  Then reboot.

Hope this helps! :)

Edit: Darn, TheGnomeOfMetal beat me to it!

still no deal.  :(

---

### Post by petermg on 2010-05-27
```
petermg@kids-ubuntu:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:17 memory:dfefc000-dfefdfff
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:06:25:1b:b6:10
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:2
       description: Ethernet interface
       physical id: 3
       logical name: usb0
       serial: 66:6b:16:d2:d9:dd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.100.100 link=yes multicast=yes
```

---

### Post by purelinuxuser on 2010-05-27
Post the output of the following commands again:
```
iwconfig
sudo iwlist scan
dmesg | grep -i b43
```

---

### Post by petermg on 2010-05-27
> **purelinuxuser said:**
> Post the output of the following commands again:
```
iwconfig
sudo iwlist scan
dmesg | grep -i b43
```

```
petermg@kids-ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

vboxnet0  no wireless extensions.

usb0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```

```
petermg@kids-ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

vboxnet0  Interface doesn't support scanning.

usb0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

petermg@kids-ubuntu:~$ dmesg | grep -i b43
[    1.232336] b43-pci-bridge 0000:02:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[10752.450027] b43legacy-phy0: Broadcom 4301 WLAN found
[10752.472014] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[10752.472039] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2053, Revision 2
[10752.496050] b43legacy-phy0 debug: Radio initialized
[10752.848483] b43legacy-phy1: Broadcom 4301 WLAN found
[10752.872017] b43legacy-phy1 debug: Found PHY: Analog 0, Type 1, Revision 4
[10752.872043] b43legacy-phy1 debug: Found Radio: Manuf 0x17F, Version 0x2053, Revision 2
[10752.896383] b43legacy-phy1 debug: Radio initialized
[10753.128044] b43legacy ssb0:0: firmware: requesting b43legacy/ucode2.fw
[10753.196496] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[10753.224917] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[10753.332029] b43legacy-phy1: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[10753.389091] b43legacy-phy1 debug: Chip initialized
[10753.389360] b43legacy-phy1 debug: 30-bit DMA initialized
[10753.395433] b43legacy-phy1 warning: LEDs: Unknown behaviour 0x2B
[10753.395440] b43legacy-phy1 warning: LEDs: Unknown behaviour 0x78
[10753.395443] b43legacy-phy1 warning: LEDs: Unknown behaviour 0x2E
[10753.395446] b43legacy-phy1 warning: LEDs: Unknown behaviour 0x19
[10753.395474] b43legacy-phy1 debug: Wireless interface started
[10753.395503] b43legacy-phy1: Radio hardware status changed to DISABLED
[10753.395508] b43legacy-phy1 debug: Radio initialized
[10753.399328] b43legacy-phy1 debug: Adding Interface type 2
[10753.432016] b43legacy-phy1: Radio turned on by software
[10753.432023] b43legacy-phy1: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[10753.432326] b43legacy-phy1 debug: Removing Interface type 2
[10753.432362] b43legacy-phy1 debug: Wireless interface stopped
[10753.432502] b43legacy-phy1 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[10753.432550] b43legacy-phy1 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[10753.432591] b43legacy-phy1 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[10753.440031] b43legacy-phy1 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[10753.448020] b43legacy-phy1 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[10753.456017] b43legacy-phy1 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[10753.464018] b43legacy-phy1 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[10753.472012] b43legacy-phy1 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[10753.480023] b43legacy-phy1 debug: Radio initialized
[10753.480036] b43legacy-phy1 debug: Radio initialized
petermg@kids-ubuntu:~$
```

---

### Post by purelinuxuser on 2010-05-27
```
[10753.395503] b43legacy-phy1: Radio hardware status changed to DISABLE
[10753.432023] b43legacy-phy1: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
```

These two messages are the key.  Apparently the wireless is manually disabled in some way.

[LIST]
[*]Check the BIOS to see if wifi is enabled
[*]Look for a physical wifi switch on your laptop and be sure it is ON
[*]Try pressing the wifi enable/disable key on your laptop (usually Fn+F8, look for a little antenna symbol)
[/LIST]
Other than that, drivers look all good!  Good luck ;)

---

### Post by petermg on 2010-05-27
> **purelinuxuser said:**
> ```
[10753.395503] b43legacy-phy1: Radio hardware status changed to DISABLE
[10753.432023] b43legacy-phy1: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
```

These two messages are the key.  Apparently the wireless is manually disabled in some way.

[LIST]
[*]Check the BIOS to see if wifi is enabled
[*]Look for a physical wifi switch on your laptop and be sure it is ON
[*]Try pressing the wifi enable/disable key on your laptop (usually Fn+F8, look for a little antenna symbol)
[/LIST]
Other than that, drivers look all good!  Good luck ;)

But this is on my desktop! LOL!!!  It's a PCI card :(  I reset my bios settings to default, but there are no wifi specific settings in my bios.

---

### Post by purelinuxuser on 2010-05-27
> **petermg said:**
> But this is on my desktop! LOL!!!  It's a PCI card :(  I reset my bios settings to default, but there are no wifi specific settings in my bios.

LOL desktop?  Uhmm... is there a button on the card? :P

---

### Post by petermg on 2010-05-28
> **purelinuxuser said:**
> LOL desktop?  Uhmm... is there a button on the card? :P

I pulled it out last night and looked all over it.  No buttons or switches.  It's a linksys PCI WMP11 v 2.7


???:confused:

---

### Post by purelinuxuser on 2010-05-29
Hmm... I guess we'll have to try a different driver.  Plug in to Ethernet (again) and go to System > Hardware Drivers.  There should be a "Broadcom STA" driver available.  Install it, reboot, and post the output of the following commands:
```
iwconfig
sudo iwlist scan
lshw -c newtork
dmesg | grep -i sta
```
(yeah, things are a bit repetitive...)

---

### Post by petermg on 2010-06-02
> **purelinuxuser said:**
> Hmm... I guess we'll have to try a different driver.  Plug in to Ethernet (again) and go to System > Hardware Drivers.  There should be a "Broadcom STA" driver available.  Install it, reboot, and post the output of the following commands:
```
iwconfig
sudo iwlist scan
lshw -c newtork
dmesg | grep -i sta
```
(yeah, things are a bit repetitive...)

there is no STA driver available... :confused:

---

### Post by purelinuxuser on 2010-06-02
Try ndiswrapper:

[LIST=1]
[*]Plug into Ethernet, install ndisgtk, ndiswrapper-utils1.9, and ndiswrapper-common from Synaptic.
[*]Download the **Windows XP** driver for your wireless card
[*]Extract the *.exe file you downloaded, look for an *.inf file (usually in a folder called DRIVER or something similar)
[*]Go to System > Administration > Windows Wireless Drivers
[*]Click "Install Driver," browse for the *.inf file from earlier
[*]Reboot
[/LIST]
Hopefully things will work properly, otherwise post
```
lshw -c network
```

---

### Post by petermg on 2010-06-04
> **purelinuxuser said:**
> Try ndiswrapper:

[LIST=1]
[*]Plug into Ethernet, install ndisgtk, ndiswrapper-utils1.9, and ndiswrapper-common from Synaptic.
[*]Download the **Windows XP** driver for your wireless card
[*]Extract the *.exe file you downloaded, look for an *.inf file (usually in a folder called DRIVER or something similar)
[*]Go to System > Administration > Windows Wireless Drivers
[*]Click "Install Driver," browse for the *.inf file from earlier
[*]Reboot
[/LIST]
Hopefully things will work properly, otherwise post
```
lshw -c network
```


But that's how I originally installed it...(after the Ubuntu hardware driver didn't bring it up) :confused:

---

### Post by purelinuxuser on 2010-06-04
Try running the following commands:
```
sudo rmmod b43
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```
They _may_ fix things, but wireless won't work upon reboot.  Tell me if these commands work, and if they don't, post any error messages.

---

