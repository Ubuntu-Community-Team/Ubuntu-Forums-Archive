---
title: "[SOLVED] Unable to get Wireless to Work at All on Toshiba Satellite"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by Treelvr on 2008-12-30
I've had Ubuntu 8.10 on desktop working great for 2 mths. Works great, would kill off XP completely but can't get Frontpage to work at all either thru WINE or play on linux. But not the problem.
Bought wife new laptop. Toshiba Satellite. And I swear that it takes Vista 5 min just to load. Wife gotten used to Ubuntu on desktop. Asked me to install on laptop. First try used CD and guided to do dual boot. Wiped disk clean installed ubuntu on whole HD. Couldn't get wireless to work at all. Reinstalled Vista wireless works fine. This time used wubi installed fine dual boot. But try as I may I can't get wireless to work. Wired no problem Read about &#8220;network manager&#8221; under prefs. Only have &#8220;network Configuration&#8221; and Network Proxy&#8221;Under admin only have &#8220;Network Tools&#8221;. There is a little network sign on top bar. Hardware shows support for atheros 802.11 wireless.
First try downloaded 64 bit driver, then installed &#8220;windows wireless drivers&#8221; and installed Dld driver. No change.
Next &#8220;Wifi radar&#8221;- failed to execute su-to-root.
Next &#8220; Madwifi&#8221; but can't find it on any menu nor can find a way online to use or config.
Read about &#8220;Wireless Assistant&#8221; Dld different versions but synaptic refused to install
Wired no problems. See fine on &#8220;Networks connections&#8221; On wireless I've added SSID I've tried no security, WEP WPA and change router accordingly and still no change.
What am I doing wrong?? It seems like its either not seeing the built in wifi, or its not turning on, or the software not connecting.

---

### Post by pytheas22 on 2008-12-30
There's probably just no driver available for the card.  In most cases Ubuntu comes with drivers already built in, but with newer machines you may need to install a driver yourself.

If you could please open up a terminal from the Applications>Accessories menu and post the output of the following commands, it will provide the information necessary for us to tell you how to get the card working:
```

lspci -nn
lshw -C Network
uname -rm
dmesg | grep -e ath -e adio
```

---

### Post by Treelvr on 2008-12-30
pharmgirl@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
0c:04.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
0c:04.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
0c:04.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
0c:04.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]
pharmgirl@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:36:bd:c1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.103 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ce:3c:90:34:a4:4d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
pharmgirl@ubuntu:~$ uname -rm
2.6.27-9-generic x86_64
pharmgirl@ubuntu:~$ dmesg | grep -e ath -e adio

---

### Post by pytheas22 on 2008-12-31
Sorry for the slow response.

This card should be supported out-of-the-box in Ubuntu 8.10.  It looks like perhaps the module is not loading for some reason.  Please post the output of these commands so that I can see what happens when you manually load the module:
```

lsmod | grep ath
sudo modprobe ath_pci
dmesg | tail -50
sudo iwlist scan
```

---

### Post by Treelvr on 2008-12-31
pharmgirl@ubuntu:~$ lsmod | grep ath
ath_pci               109168  0 
wlan                  234784  1 ath_pci
ath_hal               225904  1 ath_pci
pharmgirl@ubuntu:~$ sudo modprobe ath_pci
pharmgirl@ubuntu:~$ dmesg | tail -50
[   18.441531] EXT3 FS on loop0, internal journal
[   26.750781] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:976552k
[   26.960983] type=1505 audit(1230744181.027:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4115
[   27.117682] type=1505 audit(1230744181.183:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4120
[   27.117898] type=1505 audit(1230744181.183:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4120
[   27.276385] ip_tables: (C) 2000-2006 Netfilter Core Team
[   27.933635] ACPI: WMI: Mapper loaded
[   28.959966] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   29.153169] ppdev: user-space parallel port driver
[   32.231730] Bluetooth: Core ver 2.13
[   32.234173] NET: Registered protocol family 31
[   32.234179] Bluetooth: HCI device and connection manager initialized
[   32.234183] Bluetooth: HCI socket layer initialized
[   32.250448] Bluetooth: L2CAP ver 2.11
[   32.250454] Bluetooth: L2CAP socket layer initialized
[   32.259844] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   32.259851] Bluetooth: BNEP filters: protocol multicast
[   32.281445] Bridge firewalling registered
[   32.282272] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   32.290221] Bluetooth: SCO (Voice Link) ver 0.6
[   32.290227] Bluetooth: SCO socket layer initialized
[   32.497844] Bluetooth: RFCOMM socket layer initialized
[   32.498670] Bluetooth: RFCOMM TTY layer initialized
[   32.498677] Bluetooth: RFCOMM ver 1.10
[   36.382908] [drm] Initialized drm 1.1.0 20060810
[   36.389696] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   36.389707] pci 0000:00:02.0: setting latency timer to 64
[   36.391542] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   36.620405] r8169: eth0: link down
[  114.468024] usb 4-2: new low speed USB device using uhci_hcd and address 2
[  114.670848] usb 4-2: configuration #1 chosen from 1 choice
[  114.791813] usbcore: registered new interface driver hiddev
[  114.825373] input: HID 1241:1177 as /devices/pci0000:00/0000:00:1d.0/usb4/4-2/4-2:1.0/input/input10
[  114.848109] input,hidraw0: USB HID v1.00 Mouse [HID 1241:1177] on usb-0000:00:1d.0-2
[  114.849337] usbcore: registered new interface driver usbhid
[  114.850097] usbhid: v2.6:USB HID core driver
[  203.242354] NET: Registered protocol family 10
[  203.244821] lo: Disabled Privacy Extensions
[  203.245934] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  217.594773] r8169: eth0: link up
[  217.595380] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  217.706477] NET: Registered protocol family 17
[  228.360026] eth0: no IPv6 routers present
[  262.820717] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  262.834479] wlan: 0.9.4
[  262.842322] ath_pci: 0.9.4
[  262.842577] ath_pci 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  262.842595] ath_pci 0000:05:00.0: setting latency timer to 64
[  262.891506] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[  262.891527] ath_pci 0000:05:00.0: PCI INT A disabled
pharmgirl@ubuntu:~$ sudo iwlist scan

---

### Post by pytheas22 on 2008-12-31
Thanks, that gives a better idea of what's wrong.  These lines from dmesg in particular are worth noting:
```

[ 262.842577] ath_pci 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 262.842595] ath_pci 0000:05:00.0: setting latency timer to 64
[ 262.891506] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[ 262.891527] ath_pci 0000:05:00.0: PCI INT A disabled
```

They mean that for some reason the driver for your card doesn't think that it supports your device.  This is a well-known issue with some Atheros cards, and seems to result from the fact that Atheros ships different devices with the same device IDs, which confuses the driver.

But that's all just FYI.  In order to resolve your problem, let's first try loading the ath9k driver in place of ath_pci.  ath9k is a newer driver that may support your card better.  Please run these commands to load it, and post all output:
```

sudo modprobe -r ath_pci ath9k
sudo modprobe ath9k
dmesg | grep -e ath -e wlan
iwconfig
```

If this works, we can make the solution permanent.  If ath9k doesn't fix it, there are other options.

---

### Post by Treelvr on 2008-12-31
I was able to use a post I found on this board about madwifi and was able to get it to work.
Thank You for your help.

Tim

---

### Post by pytheas22 on 2008-12-31
I'm glad you got it fixed.

For the sake of anyone else experiencing the same problem, could you please provide a link to the thread that solved it for you?

---

### Post by Treelvr on 2008-12-31
This thread solved it for me: [http://ubuntuforums.org/showthread.php?t=902860&page=2](http://ubuntuforums.org/showthread.php?t=902860&page=2)

Thank you again.

Tim:D

---

