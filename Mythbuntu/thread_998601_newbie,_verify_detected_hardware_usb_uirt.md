---
title: "newbie, verify detected hardware usb uirt"
date: 2008-12-01
forum: Mythbuntu
---

### Post by phroman on 2008-12-01
Hey all, new to Linux and obviously Mythbuntu, trying to set up an ir blaster to control my direct tv receiver.  I have my snapstream firefly remote working but cannot get my usb uirt blaster to work.  I've  read it's supported natively, but I can't figure this out.  In MCC, if I click the checkbox to Enable IR Transmitter, I can choose USB UIRT2.  Mine is a model USB UIRT 0038, it's about 2 years old, anyone know if it's not supported?

It's plugged into a usb port, if I point a remote at it and hit a button it responds with it's own blinking red light.  Possibly just because it has power??  So, I first want to see if it's recognized/configured properly, right?

remember, I'm about a week into Linux...   :)\

At terminal I typed:  dmesg | grep -i usb

```
[    2.969660] usbcore: registered new interface driver usbfs
[    2.969698] usbcore: registered new interface driver hub
[    3.001946] usbcore: registered new device driver usb
[    3.035903] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    3.045393] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.045645] usb usb1: configuration #1 chosen from 1 choice
[    3.045672] hub 1-0:1.0: USB hub found
[    3.063199] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.253024] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    3.310377] usb usb2: configuration #1 chosen from 1 choice
[    3.310405] hub 2-0:1.0: USB hub found
[    3.708029] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    3.922619] usb 2-1: configuration #1 chosen from 1 choice
[    4.100041] usb 2-2: new low speed USB device using ohci_hcd and address 3
[    4.328346] usb 2-2: configuration #1 chosen from 1 choice
[    4.504021] usb 2-3: new low speed USB device using ohci_hcd and address 4
[    4.718340] usb 2-3: configuration #1 chosen from 1 choice
[    5.024023] usb 2-4: new full speed USB device using ohci_hcd and address 5
[    5.238331] usb 2-4: configuration #1 chosen from 1 choice
[    5.244577] usbcore: registered new interface driver hiddev
[    5.250531] input: B16_b_02 USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input1
[    5.253561] input,hidraw0: USB HID v1.10 Mouse [B16_b_02 USB-PS/2 Optical Mouse] on usb-0000:00:02.0-1
[    5.265526] input:   USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input2
[    5.265938] input,hidraw1: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:02.0-2
[    5.288248] input:   USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.1/input/input3
[    5.288644] input,hidraw2: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:02.0-2
[    5.288672] usbcore: registered new interface driver usbhid
[    5.288676] usbhid: v2.6:USB HID core driver
[   13.099428] lirc_atiusb: USB remote driver for LIRC $Revision: 1.69 $
[   13.099432] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[   13.143006] usbcore: registered new interface driver usbserial
[   13.143040] usbserial: USB Serial support registered for generic
[   13.143088] usbcore: registered new interface driver usbserial_generic
[   13.143090] usbserial: USB Serial Driver core
[   13.164570] usbserial: USB Serial support registered for FTDI USB Serial Device
[   13.170162] lirc_atiusb[4]: X10 Wireless Technology Inc USB Receiver on usb2:4
[   13.182269] ftdi_sio 2-4:1.0: FTDI USB Serial Device converter detected
[   13.182653] usb 2-4: FTDI USB Serial Device converter now attached to ttyUSB0
[   13.182684] usbcore: registered new interface driver lirc_atiusb
[   13.183244] usbcore: registered new interface driver ftdi_sio
[   13.183247] ftdi_sio: v1.4.3:USB FTDI Serial Converters Driver
[ 6351.909198] usbhid: event field not found
[ 6351.933204] usbhid: event field not found
```

I'm still trying to decipher this output but it looks like my firefly remote is ttyUSB0.  Shouldn't there be something similar for the usb uirt blaster?  I've run irw at the terminal but it shows no output. I've tried to manually edit my /etc/lirc/hardware.conf file but no luck.  I'm not sure what I should be entering for the values for ENABLE TRANSMITTER.  

Here's my /etc/lirc/hardware.conf file

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Snapstream X10 RF"
REMOTE_MODULES="lirc_dev lirc_atiusb"
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="atiusb/lircd.conf.atiusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="USB-UIRT2 : Direct TV Receiver"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="usb_uirt_raw"
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"


I'll try to keep my posts short and tackle things one step at a time, any help would be great, thanks!  :KS

---

### Post by phroman on 2008-12-04
Ok, soooooo, yea...  Hey, maybe I'm posting in the wrong place here.  Any tips on where to post this?  Thanks for any help.  :p

---

