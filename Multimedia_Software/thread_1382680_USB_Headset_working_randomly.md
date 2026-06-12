---
title: "USB Headset working randomly"
date: 2010-01-16
forum: Multimedia Software
---

### Post by penbeuz on 2010-01-16
Hi,
My Plantronics headset is detected randomly by the system, I've been searching for hours without solution, however i finaly got to thinking that there may be a problem with snd-usb-audio

```

uname -a
Linux cesan 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.

 lspci | grep [Aa]udio && lsusb | grep [Aa]udio
00:1d.0 Audio device: ALi Corporation High Definition Audio/AC'97 Host Controller (rev 02)

lsusb
Bus 003 Device 005: ID 047f:c001 Plantronics, Inc. 
Bus 003 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 002: ID 03f0:0604 Hewlett-Packard DeskJet 840c
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

cat /proc/asound/cards
 0 [M5461          ]: HDA-Intel - HDA ULI M5461
                      HDA ULI M5461 at 0xcbff8000 irq 22
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 5

tail /var/log/messages

Jan 16 15:57:26 localhost kernel: [26498.148264] usb 1-2.2: new full speed USB device using ehci_hcd and address 13
Jan 16 15:57:26 localhost kernel: [26498.240742] usb 1-2.2: configuration #1 chosen from 1 choice
Jan 16 15:57:26 localhost kernel: [26498.241478] snd-usb-audio: probe of 1-2.2:1.0 failed with error -5
Jan 16 15:57:26 localhost kernel: [26498.242571] input: HID 047f:c001 as /devices/pci0000:00/0000:00:1c.3/usb1/1-2/1-2.2/1-2.2:1.3/input/input13
Jan 16 15:57:26 localhost kernel: [26498.242657] generic-usb 0003:047F:C001.000A: input,hidraw2: USB HID v1.00 Device [HID 047f:c001] on usb-0000:00:1c.3-2.2/input3

```

on my wife's laptop I've got the following
```

uname -a
Linux cecile-laptop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.

Jan 16 15:27:44 cecile-laptop kernel: [164381.784048] usb 6-2: new full speed USB device using uhci_hcd and address 3
Jan 16 15:27:44 cecile-laptop kernel: [164381.938064] usb 6-2: configuration #1 chosen from 1 choice
Jan 16 15:27:44 cecile-laptop kernel: [164381.950707] input: HID 047f:c001 as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.3/input/input37
Jan 16 15:27:44 cecile-laptop kernel: [164381.950841] generic-usb 0003:047F:C001.0002: input,hidraw1: USB HID v1.00 Device [HID 047f:c001] on usb-0000:00:1d.0-2/input3
Jan 16 15:27:44 cecile-laptop kernel: [164382.067444] usbcore: registered new interface driver snd-usb-audio
Jan 16 15:27:56 cecile-laptop pulseaudio[4681]: ratelimit.c: 56 events suppressed
Jan 16 15:43:47 cecile-laptop kernel: [165344.496102] usb 6-2: USB disconnect, address 3

``` 

Any idea of why the sound card is not loaded?
When usb headset is detected I got the following:

```

lsusb
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 047f:c001 Plantronics, Inc. 
Bus 003 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 002: ID 03f0:0604 Hewlett-Packard DeskJet 840c
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

cat /proc/asound/cards
 0 [M5461          ]: HDA-Intel - HDA ULI M5461
                      HDA ULI M5461 at 0xcbff8000 irq 22
 1 [U0x47f0xc001   ]: USB-Audio - USB Device 0x47f:0xc001
                      USB Device 0x47f:0xc001 at usb-0000:00:1c.1-3, full speed
 2 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 5

```

---

### Post by penbeuz on 2010-01-18
system tried tu use slot 1 for the card, I forced it to use slot 2

fichier /etc/modprobe.d/usb-headset.conf

```
# Set usb headset as second device
alias snd-card-2 snd-usb-audio
options snd_usb_audio index=2
# Make sure that snd_usb_audio is loaded before usbhid
install usbhid modprobe  snd-usb-audio; modprobe --ignore-install usbhid
```

---

