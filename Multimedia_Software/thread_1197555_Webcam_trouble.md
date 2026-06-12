---
title: "Webcam trouble"
date: 2009-06-26
forum: Multimedia Software
---

### Post by comradejanus on 2009-06-26
Hi

Just bought a HiPoint 5MP web cam.

Problem is, I've tried plugging it into a computer running ubuntu 9.04 and 8.10 and it just doesn't detect it when I plug it into the usb.

I'll also tried running EasyCam but no help there. It just says no webcam detected.

Is there any hope for me to get it working in ubuntu? Or should I just send it back and get another one? I know my fault, I should have checked online for a compatibility rating.

Anyway thanks in advance for any help.

---

### Post by josteinaj on 2009-06-26
In a terminal, write 'lsusb' to list USB-devices and see if it pops up in that list. Also, after connecting the camera, write 'dmesg' in a terminal and post the part concerning the webcam at the end of the output here. It is useful debugging information.

---

### Post by comradejanus on 2009-06-26
Thank you very much for your help.

Yes, By typing 'lsusb' before and after plugging the webcam in, I have determined that It is the entry:

Bus 002 Device 005: ID 0c45:62f0 Microdia 

After typing 'dmesg' I get:



[  154.356031] usb 2-3: new high speed USB device using ehci_hcd and address 5
[  154.519089] usb 2-3: configuration #1 chosen from 1 choice
[  154.740499] Linux video capture interface: v2.00
[  154.764377] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62f0)
[  154.766790] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:02.1/usb2/2-3/2-3:1.0/input/input6
[  154.772157] usbcore: registered new interface driver uvcvideo
[  154.772166] USB Video Class driver (v0.1.0)


Well at least the computer is definitely registering it to be there, but don't know how to proceed from here.

---

### Post by comradejanus on 2009-06-26
Ah, on closer inspection, the capture works fine when running aMsn or skype.

Thanks for your help and insight into the workings of linux anyway.

---

