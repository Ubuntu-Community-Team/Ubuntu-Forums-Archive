---
title: "Installing Digicom DigiTune S USB key"
date: 2011-01-02
forum: Multimedia Software
---

### Post by SteMMo on 2011-01-02
Hi all,
i'm trying to install Digicom DigiTune S USB key.

Linux ghilba 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010 i686 GNU/Linux

Inserting the key i see:
[ 3233.008095] usb 1-4: new high speed USB device using ehci_hcd and address 4
[ 3233.145186] usb 1-4: configuration #1 chosen from 1 choice


stefano@ghilba:~$ lsusb
Bus 003 Device 002: ID 2001:3a02 D-Link Corp. [hex] DWL-G132
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13d3:3219 IMC Networks DTV-DVB UDTT7049 - DVB-T Driver(Without HID)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I typed:
sudo modprobe dvb-usb
sudo modprobe dvb-usb-vp7045


stefano@ghilba:~$ lsmod | grep dvb
dvb_usb_vp7045          7403  0 
dvb_usb                14457  1 dvb_usb_vp7045
dvb_core               86206  1 dvb_usb

I have no devices under /dev/dvb or similar ....
I installed kaffeine but it doesn't see any source

Any idea ?

---

