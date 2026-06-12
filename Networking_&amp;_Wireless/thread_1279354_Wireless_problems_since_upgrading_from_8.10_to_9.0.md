---
title: "Wireless problems since upgrading from 8.10 to 9.04"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by deglog on 2009-09-30
Hi,

On an HP 530, wireless used to be OK. But since I upgraded to 9.04 I can't connect to any wireless networks ('Wireless Networks' is grayed out in the Network Manager Applet - Gnome)

>iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

>sudo lshw -C network

  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:c1:91:98
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=full firmware=N/A ip=62.254.13.2 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:d8:7b:e2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

>dmesg | grep "wlan0"

[  149.172460] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  555.125063] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  573.108745] ADDRCONF(NETDEV_UP): wlan0: link is not ready

>sudo iwlist wlan0 scan

wlan0     No scan results

---

### Post by Iowan on 2009-09-30
What kind of wireless chipset? Unless I'm misreading or missing details, Ubuntu doesn't seem to know, either.

---

### Post by Ayuthia on 2009-09-30
What does:
```
dmesg|grep b43
```say?

---

### Post by deglog on 2009-10-01
Using the Broadcom B43 wireless driver

>dmesg| grep b43

[    3.565890] b43-pci-bridge 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.565902] b43-pci-bridge 0000:10:00.0: setting latency timer to 64
[   16.386073] b43-phy0: Broadcom 4311 WLAN found
[   30.598065] input: b43-phy0 as /devices/virtual/input/input8
[   30.648065] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   30.802294] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   30.837003] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   30.883496] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   31.020422] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   31.108525] Registered led device: b43-phy0::tx
[   31.108545] Registered led device: b43-phy0::rx
[   31.108569] Registered led device: b43-phy0::radio
[   31.124041] b43-phy0: Radio turned on by software
[   31.600045] b43-phy0: Radio hardware status changed to DISABLED
[   31.684049] b43-phy0: Radio turned on by software
[   31.684053] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.

Then I clicked 'enable wireless'

>dmesg| grep b43

[    3.565890] b43-pci-bridge 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.565902] b43-pci-bridge 0000:10:00.0: setting latency timer to 64
[   16.386073] b43-phy0: Broadcom 4311 WLAN found
[   30.598065] input: b43-phy0 as /devices/virtual/input/input8
[   30.648065] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   30.802294] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   30.837003] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   30.883496] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   31.020422] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   31.108525] Registered led device: b43-phy0::tx
[   31.108545] Registered led device: b43-phy0::rx
[   31.108569] Registered led device: b43-phy0::radio
[   31.124041] b43-phy0: Radio turned on by software
[   31.600045] b43-phy0: Radio hardware status changed to DISABLED
[   31.684049] b43-phy0: Radio turned on by software
[   31.684053] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[ 1078.305415] input: b43-phy0 as /devices/virtual/input/input9
[ 1078.476071] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1078.562803] Registered led device: b43-phy0::tx
[ 1078.562823] Registered led device: b43-phy0::rx
[ 1078.562843] Registered led device: b43-phy0::radio
[ 1079.308060] b43-phy0: Radio hardware status changed to DISABLED

---

### Post by Ayuthia on 2009-10-01
The message in your post is saying that either the BIOS has the wireless card turned off or else the switch on your laptop is not currently turned on.  You might try switching your wireless card switch on your laptop a few times (or just once if you see it off) just to make sure that it is on.  Then if it does not start up, check the BIOS.

---

### Post by deglog on 2009-10-01
Thanks Ayuthia. Its the BIOS. The laptop is dual boot with Vista. In Vista I disabled wireless, which changed something in the BIOS so it didn't work in Ubuntu either.

Nothing to do with upgrading to 9.04 after all.

---

### Post by deglog on 2009-10-01
Now 

>dmesg| grep b43

[   30.616039] b43-phy0: Radio turned on by software

instead of 'Radio status changed to DISABLED'. With hindsight its obvious that this line is important, but I honestly thought 'radio' whats that got to do with it? do I have a radio in my laptop?

---

### Post by Ayuthia on 2009-10-01
> **deglog said:**
> Now 

>dmesg| grep b43

[   30.616039] b43-phy0: Radio turned on by software

instead of 'Radio status changed to DISABLED'. With hindsight its obvious that this line is important, but I honestly thought 'radio' whats that got to do with it? do I have a radio in my laptop?

It is quite common to see that message show up in the Linux forums.  I am just waiting for the day when someone reports that they think they can hear a faint sound of a radio station playing.

---

