---
title: "Webcam ToUcam II is not recognized"
date: 2006-11-16
forum: Multimedia &amp; Video
---

### Post by huygens on 2006-11-16
I have a webcam Philips ToUcam II (ov511 driver, model PCVC820K/00), I am using Ubuntu 6.10 (aka Edgy Eft) and, as you guess, my webcam does not work.

So I plugged the webcam and as Ekiga did not see any device, I have check my dmesg, here it is:
```
[17181651.888000] usb 3-6.4: new full speed USB device using ehci_hcd and address 6
[17181651.980000] usb 3-6.4: configuration #1 chosen from 1 choice
[17181652.160000] Linux video capture interface: v1.00
[17181652.172000] drivers/media/video/ov511/ov511.c: USB OV518 video device found
[17181652.176000] drivers/media/video/ov511/ov511.c: Device revision 1
[17181652.176000] drivers/media/video/ov511/ov511.c: Compression required with OV518...enabling
[17181655.044000] drivers/media/video/ov511/ov511.c: Can't determine sensor slave IDs
[17181655.044000] drivers/media/video/ov511/ov511.c: OV518 Config failed
[17181655.044000] drivers/media/video/ov511/ov511.c: Camera initialization failed
[17181655.044000] ov511: probe of 3-6.4:1.0 failed with error -5
[17181655.044000] usbcore: registered new driver ov511
[17181655.044000] drivers/media/video/ov511/ov511.c: v1.64 for Linux 2.5 : ov511 USB Camera Driver
```So I decided to look around on the forums and wiki, and there was loads of resources. First of all, I have tried to load the module ovcamchip as instructed. This did not help.
Then I [have read]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras") that I should download the latest ov511 driver and install it. So I did it, installation works perfectly. I try it, no luck still but at least I had suddenly a device /dev/video0 which I did not before. Now the sensor is not detected...
```
[17191001.036000] ov511-2.32/ovcamchip_core.c: v2.32 : OV camera chip I2C driver
[17191003.772000] ov511-2.32/ov511_core.c: USB OV518 video device found
[17191003.776000] ov511-2.32/ov511_core.c: Device revision 1
[17191003.776000] ov511-2.32/ov511_core.c: Compression required with OV518...enabling
[17191007.232000] ov511-2.32/ov511_core.c: Device at usb-0000:00:02.2-6.4 registered to minor 0
[17191007.232000] usbcore: registered new driver ov511
[17191007.232000] ov511-2.32/ov511_core.c: v2.32 : ov511 USB Camera Driver (V4L2 disabled)
[17191046.136000] ov511-2.32/ov511_core.c: No sensor is detected yet

```So I go again looking around, and I found this resource: [http://home.insightbb.com/~foolsh/]("http://home.insightbb.com/%7Efoolsh/")
So cool, this is maybe my problem. I download the new driver, install it (as described directly on this page, or directly by following the instructions from the driver developer). And now I am exactly in the same state as I was with the original Ubuntu driver:
```
[17193150.508000] Linux video capture interface: v1.00
[17193150.512000] ov51x-jpeg-0.5.4/ov51x.c: USB OV518 video device found
[17193150.512000] ov51x-jpeg-0.5.4/ov51x.c: Device revision 1
[17193150.516000] ov51x-jpeg-0.5.4/ov51x.c: Compression required with OV518...enabling
[17193155.648000] ov51x-jpeg-0.5.4/ov51x.c: Can't determine sensor slave IDs
[17193155.648000] ov51x-jpeg-0.5.4/ov51x.c: OV518 Config failed
[17193155.648000] ov51x-jpeg-0.5.4/ov51x.c: Camera initialization failed
[17193155.648000] ov51x: probe of 3-6.4:1.0 failed with error -5
[17193155.652000] usbcore: registered new driver ov51x
[17193155.652000] ov51x-jpeg-0.5.4/ov51x.c: v1.65-1.11-mark : ov51x USB Camera Driver

```Any help would be greatly appreciated.

Huygens

PS: after each manipulation, I have tried to see if the webcam could work using xawtv and ekiga.

---

