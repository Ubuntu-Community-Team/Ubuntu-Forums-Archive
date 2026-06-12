---
title: "USB CDMA modem not recognized"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by eriksank on 2009-04-22
I cannot get my USB CDMA modem to work under Ubuntu Intrepid.

The device shows up in lsusb:

# lsusb
Bus 004 Device 025: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x Composite Device


The device shows up in /var/log/messages:

# tail /var/log/messages
[ 4051.771237] usbserial: USB Serial support registered for cp2101
[ 4051.772355] cp2101 4-2:1.0: cp2101 converter detected
[ 4051.884191] usb 4-2: reset full speed USB device using uhci_hcd and address 25
[ 4052.030014] usb 4-2: cp2101 converter now attached to ttyUSB0
[ 4052.030842] usbcore: registered new interface driver cp2101
[ 4052.030855] cp2101: Silicon Labs CP2101/CP2102 RS232 serial adaptor driver v0.07


The device shows up in dmesg:

#dmesg
[ 3417.063850] usbserial: USB Serial support registered for cp2101
[ 3417.063890] cp2101 4-2:1.0: cp2101 converter detected
[ 3417.172036] usb 4-2: reset full speed USB device using uhci_hcd and address 25
[ 3417.321873] usb 4-2: cp2101 converter now attached to ttyUSB0
[ 3417.322202] usbcore: registered new interface driver cp2101


However, when I mount the usb file system, it fails to show up:

# mount -t usbfs usbdevfs /proc/bus/usb
# cat /proc/bus/usb/devices

The device does not show up in the list of usb devices, listed in /proc/bus/usb/devices.


I have configured wvdial.conf as following:

[Dialer excell]
Modem = /dev/ttyUSB0
Dial Command = ATDT
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
SetVolume = 0
Modem Name = CDMA
Modem Type = USB Modem
Phone = #777
Username = excell
Password = excell
Stupid Mode = 1
FlowControl = Hardware (CRTSCTS)


When I dial out using this configuration, I get:

# wvdial excell 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

Has anybody figured out how to get this device type "Cygnal Integrated Products, Inc. CP210x Composite Device" to work in Ubuntu? Does anybody know how to fix this problem? I'd be most grateful.

---

