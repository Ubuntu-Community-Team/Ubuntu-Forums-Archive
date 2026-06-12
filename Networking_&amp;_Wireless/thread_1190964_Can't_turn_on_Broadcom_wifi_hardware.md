---
title: "Can't turn on Broadcom wifi hardware"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by DavidFourer on 2009-06-18
I think I've narrowed down my Broadcom BCM4318 wifi problem to a problem turning on the hardware.  The wifi LED light is always on.  Fn-F2 key should toggle wifi device on/off (Dell Inspiron 6000) but it does nothing.

I'm following the "WirelessTroubleShootingGuide" at
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
The driver and everything checks out until I get to this part of the guide:
> 4.2.5. Driver looks ok, device disabled
    * Newer laptops come with features to disable the wireless radio to save battery...
      Usually this is apparent by running the lshw command you see *-network:1 DISABLED or wireless=radio off

An abbreviated output from "sudo lshw -C network" on my system:
> *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3

  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0

  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0

An abbreviated output from dmesg:
> [ 2761.579534] b43-pci-bridge 0000:03:03.0: PCI INT A disabled
[ 2763.285138] b43-pci-bridge 0000:03:03.0: enabling device (0000 -> 0002)
[ 2763.285143] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2763.285149] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 2763.285171] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x4 (was 0x0, writing 0xdfdfe000)
[ 2763.285178] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x3 (was 0x0, writing 0x4000)
[ 2763.285186] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x1 (was 0x2, writing 0x106)
...
[ 2767.092054] b43-phy0: Radio turned on by software
[ 2767.092060] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[ 2777.768658] input: b43-phy0 as /devices/virtual/input/input21
[ 2777.940090] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 2777.990120] Registered led device: b43-phy0::tx
[ 2777.990145] Registered led device: b43-phy0::rx
[ 2777.990171] Registered led device: b43-phy0::radio
[ 2778.044915] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2778.772082] b43-phy0: Radio hardware status changed to DISABLED

The wifi docs guide offers this advice:
> Look at the LaptopTestingTeam page on the team wiki to see if your laptop is listed with any information.
Do a Google search using terms such as manufacture, model, linux, wireless, enable, button, radio....etc. When searching and finding similar pages that don't help, use words that are used in those pages to help you search.
Go to the Ubuntu forums and ask, maybe someone else has the same laptop and knows the work around.

A little while back, I was getting a long list of wifi signals from the NetworkManager applet.  The connections were fine.  WEP encryption was fine.  I used the native driver BCM43xx without problems.  It broke with a kernel update while running Intrepid, and does not work with my Jaunty install.

Am I on the right track?  Any ideas?

---

### Post by Ayuthia on 2009-06-18
It looks like you are on the right track.  By any chance is there a wireless option in your BIOS setup?

---

### Post by DavidFourer on 2009-06-18
> **Ayuthia said:**
> It looks like you are on the right track.  By any chance is there a wireless option in your BIOS setup?

Fixed it!  The last item in the BIOS setup (F2 at the start of boot sequence) is Wireless Devices.  I switched it to "ON when operating system loads".  This was the default, so I don't know how it got changed.  I still can't use the Fn key to change it, but now I have wifi and roaming for signals, in NetworkManager.  My connection is fine.

Thanks

---

