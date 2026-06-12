---
title: "Internal Wireless malfunction - Ubuntu 12.04 LTS - HP Pavilion g6 - Broadcom BCM4313"
date: 2012-07-12
forum: Networking &amp; Wireless
---

### Post by clovisdecruz on 2012-07-12
P.S. I had just posted this issue as a question on Launchpad Q#202918. 



Internal Wireless malfunction - Ubuntu 12.04 LTS - HP Pavilion g6 - Broadcom BCM4313
 For the past 3 days my wireless connection has been malfunctioning.  It starts and works for a little while and then it just fails. But again  it works after I have shutdown the laptop for some hours and then again  after a few minutes it fails. Could it be related to heat? Could it be  airflow or some fan which is not working? Is there a way to check the  system temperature or fan speed in Ubuntu or should it be BIOS? My BB is  able to access the same wireless network acess point.


 Information:
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
 Subsystem: Hewlett-Packard Company Device 1483
 Flags: fast devsel, IRQ 17
 Memory at d0200000 (64-bit, non-prefetchable) [disabled] [size=16K]
 Capabilities: <access denied>
 Kernel driver in use: wl
 Kernel modules: wl, bcma, brcmsmac
 Syslog:
Jul 12 13:01:14 clovis-HP-Pavilion-g6-Notebook-PC bluetoothd[698]: HCI dev 0 down
Jul 12 13:01:14 clovis-HP-Pavilion-g6-Notebook-PC bluetoothd[698]: Adapter /org/bluez/698/hci0 has been disabled
Jul 12 13:01:14 clovis-HP-Pavilion-g6-Notebook-PC kernel: [ 4296.032944] usb 7-1: USB disconnect, device number 11
Jul 12 13:01:14 clovis-HP-Pavilion-g6-Notebook-PC kernel: [ 4296.034514] Bluetooth: hci0 urb f0c0aa80 submission failed
Jul 12 13:01:14 clovis-HP-Pavilion-g6-Notebook-PC bluetoothd[698]: Can't init device hci0: No such device (19)
Jul 12 13:01:15 clovis-HP-Pavilion-g6-Notebook-PC bluetoothd[698]: HCI dev 0 unregistered
Jul 12 13:01:15 clovis-HP-Pavilion-g6-Notebook-PC bluetoothd[698]: Stopping hci0 event socket
Jul 12 13:01:15 clovis-HP-Pavilion-g6-Notebook-PC bluetoothd[698]: Unregister path: /org/bluez/698/hci0
Jul 12 13:01:15 clovis-HP-Pavilion-g6-Notebook-PC bluetoothd[698]: Endpoint unregistered: sender=:1.48 path=/MediaEndpoint/A2DPSink
Jul 12 13:01:15 clovis-HP-Pavilion-g6-Notebook-PC bluetoothd[698]: Endpoint unregistered: sender=:1.48 path=/MediaEndpoint/A2DPSource
Jul 12 13:01:15 clovis-HP-Pavilion-g6-Notebook-PC bluetoothd[698]: Endpoint unregistered: sender=:1.48 path=/MediaEndpoint/HFPAG
Jul 12 13:01:23 clovis-HP-Pavilion-g6-Notebook-PC kernel: [ 4305.064216] usb 7-1: new full-speed USB device number 12 using ohci_hcd
Jul 12 13:01:24 clovis-HP-Pavilion-g6-Notebook-PC bluetoothd[698]: HCI dev 0 registered
Jul 12 13:01:24 clovis-HP-Pavilion-g6-Notebook-PC bluetoothd[698]: Listening for HCI events on hci0
Jul 12 13:01:24 clovis-HP-Pavilion-g6-Notebook-PC bluetoothd[698]: HCI dev 0 up
Jul 12 13:01:24 clovis-HP-Pavilion-g6-Notebook-PC bluetoothd[698]: Adapter /org/bluez/698/hci0 has been enabled
Jul 12 13:01:24 clovis-HP-Pavilion-g6-Notebook-PC bluetoothd[698]: Endpoint registered: sender=:1.48 path=/MediaEndpoint/HFPAG
Jul 12 13:01:24 clovis-HP-Pavilion-g6-Notebook-PC bluetoothd[698]: Endpoint registered: sender=:1.48 path=/MediaEndpoint/A2DPSource
Jul 12 13:01:24 clovis-HP-Pavilion-g6-Notebook-PC bluetoothd[698]: Endpoint registered: sender=:1.48 path=/MediaEndpoint/A2DPSink

---

### Post by madvinegar on 2012-07-12
Please post the outcome of:

```
lspci
sudo lshw -c network
sudo rfkill list all
```

To check the temperature of your laptop install the following:

Sensons
```
sudo apt-get install lm-sensors
sudo sensors-detect
```
(answer "yes" to all questions).

Then install psensors
```
sudo apt-get install psensor
```


Also check the following:
Go to you router settings and try changing the 802.11b to 802.11g (or the other way around).
Try changing the broadcast channel i.e. from 6 to 9. It might be an interference problem.

---

### Post by clovisdecruz on 2012-07-12
Thanks very much for the reply madvinegar and here is the output:

lspci:
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1) (rev ff)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series]
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev ff)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)

sudo lshw -c network:
 *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 98:4b:e1:a6:91:1d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=10.10.10.5 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-generic DISABLED
       description: Wireless interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: ff
       serial: e0:2a:82:44:94:44
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.2.0-26-generic-pae firmware=N/A latency=255 link=no maxlatency=255 mingnt=255 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0200000-d0203fff

sudo rfkill list all:
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
9: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

My wireless access point only supports 2.4Ghz which is 802.11g to be precise. And it is currently set to Auto, before it was 11.

---

### Post by clovisdecruz on 2012-07-13
The issue seems to occur after a while and when the system reaches 70 degrees.

So far, two changes have been implemented to try to solve the issue:

1, Reverted the Broadcom STA wireless driver to default driver brcmsmac.

2, Changed to Wirless channel to auto.

In some case the workaround is to restart the laptop, but the probability of success is only when the laptop's temperature is operating cool i.e. 50 degrees.

---

### Post by clovisdecruz on 2012-08-08
I guess this thread can be closed as the issue does not occur any more. Driver was reverted and wireless channel is auto (5).

---

### Post by clovisdecruz on 2012-08-08
... and thank you madvinegar for your kind assistance...

---

