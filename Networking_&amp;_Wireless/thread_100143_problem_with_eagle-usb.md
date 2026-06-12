---
title: "problem with eagle-usb"
date: 2005-12-07
forum: Networking &amp; Wireless
---

### Post by Darky1983 on 2005-12-07
I'm using the eagle-usb driver, i get the device removed when downloading, videoconference or something with high bandwidth usage but no problem when surfing the web or using messenger. Sometimes get disconnected without high bandwidth usage but with same errors.
 
Vicente
 
dmesg
----------
[234030.878974] [Eagle-usb] transmit error with URB status -71
[234030.879996] [eagle-usb] eu_irq : URB canceled by user.
[234030.880024] [Eagle-usb] transmit error with URB status -71
[234030.881003] [Eagle-usb] transmit error with URB status -71
[234030.882008] [Eagle-usb] transmit error with URB status -71
[234030.882982] [Eagle-usb] transmit error with URB status -71
[234030.884056] [Eagle-usb] transmit error with URB status -71
[234030.885026] [Eagle-usb] transmit error with URB status -71
[234030.886028] [Eagle-usb] transmit error with URB status -71
[234030.887019] [Eagle-usb] transmit error with URB status -71
[234030.888026] [Eagle-usb] transmit error with URB status -71
[234030.889034] [Eagle-usb] transmit error with URB status -71
[234030.892000] [Eagle-usb] transmit error with URB status -71
[234030.991824] hub 1-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[234030.991896] usb 1-2: USB disconnect, address 39
[234030.992117] [EAGLE-USB] eu_iso_read_completion: Can't submit urb (-19)
[234030.992171] [EAGLE-USB] eu_iso_read_completion: Can't submit urb (-19)
[234030.992222] [EAGLE-USB] eu_iso_read_completion: Can't submit urb (-19)
[234030.992270] [EAGLE-USB] eu_iso_read_completion: Can't submit urb (-19)
[234030.992316] [EAGLE-USB] eu_iso_read_completion: Can't submit urb (-19)
[234030.992366] [EAGLE-USB] eu_iso_read_completion: Can't submit urb (-19)
[234031.077120] [eagle-usb] ADSL device removed
[234031.238148] usb 1-2: new full speed USB device using uhci_hcd and address 40
[234031.432740] [eagle-usb] New USB ADSL device detected, waiting for DSP code...
[234031.432774] [eagle-usb] Interface 0 accepted.
[234031.435065] [eagle-usb] created proc entry at : /proc/driver/eagle-usb/001-040

 
lsusb
--------
Bus 001 Device 039: ID 1110:900f Analog Devices Canada, Ltd (Allied Telesyn) AT-AR215 DSL Modem
Bus 001 Device 001: ID 0000:0000

lspci
-------
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C598 [Apollo MVP3] (rev 04)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C586/A/B PCI-to-ISA [Apollo VP] (rev 41)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 02)
0000:00:07.3 Bridge: VIA Technologies, Inc. VT82C586B ACPI (rev 10)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: S3 Inc. Savage 4 (rev 02)

---

