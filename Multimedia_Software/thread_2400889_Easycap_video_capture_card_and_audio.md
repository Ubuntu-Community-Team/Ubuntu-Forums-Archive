---
title: "Easycap video capture card and audio"
date: 2018-09-11
forum: Multimedia Software
---

### Post by philled on 2018-09-11
I have just purchased one of those Easycap video capture cards on eBay. These can be used to digitise old VHS tapes. There are many different types of chipsets and devices all sold as "Easycap" which makes it a bit of a lottery as to what you get. More info on this is at [https://linuxtv.org/wiki/index.php/Easycap](https://linuxtv.org/wiki/index.php/Easycap).

I think I may have got lucky as mine seems to be supported by the kernel on my Lubuntu 18.04 machine, even though it's not listed on the linuxtv page. And not only does it have video but it seems to have audio support, too. 
```

$ lsusb
Bus 001 Device 005: ID 534d:0021  
```

```

$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 1: Intel ICH - MIC ADC [NVidia CK804 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: USB20 [AV TO USB2.0], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```

$ dmesg
[   20.459510] usbcore: registered new interface driver uvcvideo
[   20.459513] USB Video Class driver (1.1.1)
[   22.273464] IPv6: ADDRCONF(NETDEV_UP): enp0s10: link is not ready
[   22.280945] IPv6: ADDRCONF(NETDEV_UP): enp0s10: link is not ready
[   22.280967] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s10: link becomes ready
[   22.346238] IPv6: ADDRCONF(NETDEV_UP): enp1s10f0: link is not ready
[   22.350133] IPv6: ADDRCONF(NETDEV_UP): enp1s10f0: link is not ready
[   22.420654] IPv6: ADDRCONF(NETDEV_UP): enp1s10f1: link is not ready
[   22.436220] IPv6: ADDRCONF(NETDEV_UP): enp1s10f1: link is not ready
[   39.035080] retire_capture_urb: 9 callbacks suppressed
[  417.824044] usb 1-2: USB disconnect, device number 2
[ 1079.768029] usb 1-10: new high-speed USB device number 5 using ehci-pci
[ 1079.926021] usb 1-10: New USB device found, idVendor=534d, idProduct=0021
[ 1079.926025] usb 1-10: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1079.926027] usb 1-10: Product: AV TO USB2.0
[ 1079.926029] usb 1-10: Manufacturer: MACROSIL
[ 1079.930385] uvcvideo: Found UVC 1.00 device AV TO USB2.0 (534d:0021)
[ 1079.931522] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[ 1079.931891] uvcvideo 1-10:1.0: Entity type for entity Processing 2 was not initialized!
[ 1079.931894] uvcvideo 1-10:1.0: Entity type for entity Camera 1 was not initialized!
```

When I try to capture some video using guvcview it looks like video and audio are supported with the video device showing up as "AV TO USB2.0", and the audio device as "AV TO USB2.0 Analogue Stereo". So all good so far!

But when I capture the video from my old tape with guvcview, I don't get any audio other than a few random clicks. I think this may be because the audio API list I can choose from is NO SOUND, PORTAUDIO or PULSEAUDIO. I'm guessing these don't work on my system, and that Alsa Audio would but there's no option for that. 

My other option to capture the video/audio is to use ffmpeg and I've tried this, but I still just get a few clicks:
```
$ sudo nice --20 ffmpeg -f alsa -i hw:2 -f video4linux2 -i /dev/video0 -r:v pal -preset ultrafast test.mp4
```


Can anyone suggest anything for how to fix this?

---

### Post by rkarpuzov on 2018-12-18
I have same device ID for two different devices (looking diff), but the same same chip.
Can anybody help to use the video capture under Linux?

---

### Post by philled on 2018-12-19
> **rkarpuzov said:**
> I have same device ID for two different devices (looking diff), but the same same chip.
Can anybody help to use the video capture under Linux?

Hi, did you try the commands I posted above? They almost worked for me - I got video just fine, but the audio didn't work. You may have better luck than me. Interested to hear how you get on.

---

### Post by siderskiy on 2019-09-19
What's the FPS the device supports.  I have the same device but its FPS is 25 (under NTFS) in Windows 10.

---

