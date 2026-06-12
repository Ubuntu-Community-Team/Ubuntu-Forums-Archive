---
title: "Hardy updates kill downloads from Nikon Coolpix 995"
date: 2008-08-26
forum: Multimedia Software
---

### Post by gnemo on 2008-08-26
Hi everyone, I have an old Nikon Coolpix 995 which is still going strong and is my only digital camera. I usually download images via a USB cable plugged into the camera and my P.C. This camera appears as a plain old USB mass storage device to the computer, and has always posed no problems under Linux in the past.

However, after updating my Hardy Heron install with all security updates, I can no longer download images from the Nikon. When I plug the camera cable into the computer, I get the familiar "A new medium has been detected" popup, but clicking "Open in New Window" gives me a Konqueror error "Could not read file Unspecified error." and a blank Konqueror window open to system:/media/camera (screenshots attached).

Running dmesg shows that a USB mass storage driver has been seen by the kernel (the last line appeared after I turned the camera off):
```

[  832.891425] usb 1-4: new full speed USB device using ohci_hcd and address 8
[  832.968083] usb 1-4: configuration #1 chosen from 1 choice
[  833.007582] usbcore: registered new interface driver libusual
[  833.022124] Initializing USB Mass Storage driver...
[  833.022294] scsi4 : SCSI emulation for USB Mass Storage devices
[  833.022384] usbcore: registered new interface driver usb-storage
[  833.022386] USB Mass Storage support registered.
[  833.022566] usb-storage: device found at 8
[  833.022568] usb-storage: waiting for device to settle before scanning
[  916.692241] usb 1-4: USB disconnect, address 8


```
I have confirmed that it is not a problem with the camera or cable: the Nikon works just fine with my wife's Mac.

By the way, other USB mass storage devices (such as my thumb drives) continue to work just fine. The Nikon is the only thing that seems to have stopped working after the security updates were applied.

Help, anyone?

TIA,

-Gnemo

---

### Post by rhobeta on 2008-09-22
I have exactly the same problem with an Olympus C-480 digital camera. I recently upgraded from kubuntu 6.06 to 8.04. On the previous version the camera was identified as a usb mass storage device and that was just fine with me - I could get access to my images. Hardy identifies the camera, but throws an error when I try to open the camera.

I hate to say this but Windows XP handles the camera just fine.

I'd appreciate any clues regarding how to deal with this.

Thanks

Ross

---

### Post by GL541 on 2009-02-22
Bump! Because I have the same problem too, with an Olympus C-480 ZOOM.

---

### Post by tmorosco on 2009-03-22
'nuther bump.  I'm having the same problem as the original poster (Nikon 995) with Intrepid (kernel 2.6.27-9-generic).

Hope I can figure it out and post back!

---

