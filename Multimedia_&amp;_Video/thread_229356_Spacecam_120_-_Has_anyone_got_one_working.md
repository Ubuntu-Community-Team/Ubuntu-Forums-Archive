---
title: "Spacecam 120 - Has anyone got one working?"
date: 2006-08-04
forum: Multimedia &amp; Video
---

### Post by ironfistchamp on 2006-08-04
Ok I have a Trust Spacecam 120. Apparently the drivers are already installed and it should work straight off. I have it working on another computer. It won't work on this one.

It registers the cam but no apps can detect it. I have a feeling it could be something to do with the USB controller. I have an NForce 4 Ultra mobo. The other computer has a Via chipset. Anyway those are the only differences between the two computers (some other hardware not linked to cam/usb is different but the OS is the same)

Can anyone help?

DMESG output
```

[17180645.264000] usb 1-10: USB disconnect, address 3
[17180654.136000] usb 1-10: new full speed USB device using ohci_hcd and address 4
[17180654.516000] sn9c102: V4L2 driver for SN9C10x PC Camera Controllers v1:1.24a
[17180654.520000] usb 1-10: SN9C10[12] PC Camera Controller detected (vid/pid 0x0C45/0x600D)
[17180654.592000] usb 1-10: PAS106B image sensor detected
[17180655.260000] usb 1-10: Initialization succeeded
[17180655.260000] usb 1-10: V4L2 device registered as /dev/video0
[17180655.260000] usb 1-10: Optional device control through 'sysfs' interface ready
[17180655.260000] usbcore: registered new driver sn9c102
[17180655.304000] usbcore: registered new driver spca5xx
[17180655.304000] drivers/usb/media/spca5xx/spca5xx-main.c: spca5xx driver 00.57.08 registered

```

Thanks

Ironfistchamp

---

