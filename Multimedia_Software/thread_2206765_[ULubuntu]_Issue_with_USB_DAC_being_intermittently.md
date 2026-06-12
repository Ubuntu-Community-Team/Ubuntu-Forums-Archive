---
title: "[U/Lubuntu] Issue with USB DAC being intermittently usable. USB driver or ALSA issue"
date: 2014-02-20
forum: Multimedia Software
---

### Post by andrewtan2 on 2014-02-20
Hi guys, I hope this is the right section to post this question.


I bought a new USB DAC - UD110v2 (sound card) recently and it has a very weird incompatibility with Ubuntu & Lubuntu.
It can seem to be registered with the OS. If it can be registered with the OS, sometimes ALSA cannot register it as a USB sound card.
The weird part is, if i insert or push the DAC slowly into the usb port (>2 second to fully plug inside the port)... there will be no problems whatsoever.

This is how _another_ USB DAC responds when inserted into port (quick insert):
As you can see, detected, descriptors are all there, registered with alsa. No issues here.
```
[  508.076058] usb 5-1: new full-speed USB device number 50 using uhci_hcd
[  508.164180] usb 5-1: New USB device found, idVendor=08bb, idProduct=2704
[  508.164188] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  508.164193] usb 5-1: Product: USB Audio DAC   
[  508.164198] usb 5-1: Manufacturer: Burr-Brown from TI              
[  508.170285] input: Burr-Brown from TI               USB Audio DAC    as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.2/input/input11
[  508.170552] hid-generic 0003:08BB:2704.0005: input,hidraw4: USB HID v1.00 Device [Burr-Brown from TI               USB Audio DAC   ] on usb-0000:00:1d.0-1/input2
[  508.512070] usbcore: registered new interface driver snd-usb-audio
```


This is how the UD110v2 responds sometimes (quick insert, completely wont work):
No descriptor and weird errors, trust me i have done everything possible on google.
```
[  643.772056] usb 5-1: new full-speed USB device number 51 using uhci_hcd
[  644.180108] usb 5-1: device not accepting address 51, error -71
[  644.292051] usb 5-1: new full-speed USB device number 52 using uhci_hcd
[  644.700117] usb 5-1: device not accepting address 52, error -71
[  644.812117] usb 5-1: new full-speed USB device number 53 using uhci_hcd
[  644.932054] usb 5-1: device descriptor read/64, error -71
[  645.156115] usb 5-1: device descriptor read/64, error -71
[  645.372118] usb 5-1: new full-speed USB device number 54 using uhci_hcd
[  645.492115] usb 5-1: device descriptor read/64, error -71
[  645.716033] usb 5-1: device descriptor read/64, error -71
```

This is how the UD110v2 responds sometimes 
(slow insert but not slow enough... registered as system device, no sound, ALSA fail to recognize and register as USB Audio device)
```
[  685.308112] usb 5-1: new full-speed USB device number 59 using uhci_hcd
[  685.610170] usb 5-1: config 1 has an invalid interface number: 3 but max is 2
[  685.610177] usb 5-1: config 1 has an invalid interface number: 3 but max is 2
[  685.610182] usb 5-1: config 1 has an invalid interface number: 3 but max is 2
[  685.610186] usb 5-1: config 1 has no interface number 2
[  685.649161] usb 5-1: New USB device found, idVendor=262a, idProduct=1112
[  685.649169] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  685.649174] usb 5-1: Product: UD110v2
[  685.649179] usb 5-1: Manufacturer: STONERACOUSTICS
[  685.668254] input: STONERACOUSTICS UD110v2 as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input12
[  685.668401] hid-generic 0003:262A:1112.0006: input,hidraw4: USB HID v1.00 Device [STONERACOUSTICS UD110v2] on usb-0000:00:1d.0-1/input0
```


Things I've done:
- Disable USB autosuspend
- Set USB initialization manually to old / new mode
- Set USB initialization to auto (both mode)
- Increase get-initial descriptor timeout -10seconds
- Reset ALSA and soundcore
- Set kernel flag IRQpoll
- Turn off & unplug laptop for an hour
- Use DAC on a powered USB HUB 
- Reset BIOS
- Test on different kernels
- Test of different OS (lubuntu/ubuntu/windows)
tons of other stuff

I have a feeling that during slow insert, the USB DAC's receiver has enough time to power up and send valid data over to the driver.
Plugging in the usual way (fast enough) will cause it to throw bad data? 
Cuz, if i insert it really really slow(2 sec at least) every time, it will work perfect.
But that's not normal behavior for any usb device. Only this one.

RECEIVER : SA9027
LDO : LP5907
CLOCK: AK8133E
DAC : PCM5102A

Laptop running Ubuntu/Lubuntu is a Macbook 2007
Anyone has any tips on how to uhh, delay? the host side registration by about 2 seconds after connection, then only attempt registration?
Also, just for information It works fine on Windows though.

---

