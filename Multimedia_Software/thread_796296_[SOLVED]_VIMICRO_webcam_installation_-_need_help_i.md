---
title: "[SOLVED] VIMICRO? webcam installation - need help identifying cam and necessary drive"
date: 2008-05-16
forum: Multimedia Software
---

### Post by renfrew on 2008-05-16
I just bought an inexpensive webcam for use on Hardy Heron... from everything I've read about Heron and cams it seemed like it would be pretty easy to get installed/configured.  So far I've had no luck though.
After some digging around I think the generic cam is based on the ViMicro ZC0302 chipset, but the latest spca5xxxx driver doesn't seem to recognize the cam.

so far I've :
- tried to install using easycam2 (no camera found, or unsupported camera)
- downloaded, compiled and installed the latest? spca5xx driver from mxhaard.free.fr (gspcav1-20071224.tar.gz) (make && sudo make install)
- sudo depmod -ae
- sudo modprobe gspca
- updated the usb ids (update-usbid)
- rebooted
- spun around three times on a large flat rock and spat over my left shoulder
- prayed to every god in every pantheon that I could think of at 1 in the morning

every thing up til rebooting seems to have worked (module is installed, lsmod lists it and video, etc.), although when I do a lsusb all i see is a listing for a Microdia device on port 6 (where the cam is plugged in) and the cam just sits there doing nothing very cam-like, other than the 6 leds being on all the time... its getting power at least and I now have a very powerful night-light lol

The cam itself came in a fairly generic box, model number DP6640 from some nameless chinese company. Bought from these guys: [http://www.factorydirect.ca/catalog/product_spec.php?pcode=DP6640](http://www.factorydirect.ca/catalog/product_spec.php?pcode=DP6640)

I've attached a pic of the cam in case anyone recognizes it and can point me in the right direction, help, please !?!?

---

### Post by milanvora2 on 2008-05-16
what is the ouptut from lsusb ?

---

### Post by renfrew on 2008-05-16
I'm not at the comp now to give you the exact output, but LSUSB reports a Microdia device on port 6 (where the cam is plugged in)

---

### Post by boballen55 on 2008-05-16
Hey, I think I just got the exact same camera (judging by the picture, it is some weird Chinese generic thing) so I'm interested in how you get it to work (I haven't even tried yet because I don't have internet at home at the moment).  Good luck.

---

### Post by renfrew on 2008-05-16
I'd really appreciate any insight anyone has into this... from looking further into this I think I need the SN9CXXX driver but can anyone confirm?

Here's the output from:
-  dmesg |tail |grep usb (shortly after plugging in the cam)
```
[  311.295247] usbcore: registered new interface driver gspca
[  406.339319] usb 1-1: USB disconnect, address 6
[41414.491498] usb 1-1: new full speed USB device using ohci_hcd and address 10
[41414.679209] usb 1-1: configuration #1 chosen from 1 choice

```

- lsusb:
```
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:7e04 Hewlett-Packard Deskjet F4100 Printer series
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 010: ID 0c45:6128 Microdia 
Bus 001 Device 009: ID 1019:0c55 Elitegroup Computer Systems (ECS) USB Flash Reader, Desknote UCR-61S2B
Bus 001 Device 008: ID 0a5c:2045 Broadcom Corp. Bluetooth Controller
Bus 001 Device 007: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 001 Device 001: ID 0000:0000  
```

- and finally lsmod | grep gspca:
```

gspca                 643792  0 
videodev               29696  1 gspca
usbcore               146924  8 gspca,usblp,usb_storage,libusual,hci_usb,ehci_hcd,ohci_hcd
```

uname -r reports as I expect:
2.6.24-17-rt

---

### Post by Gunman1982 on 2008-05-16
Seems there is a patch available for the gspca module
[http://groups.google.com/group/microdia/browse_thread/thread/bf525967f4a7b735]("http://groups.google.com/group/microdia/browse_thread/thread/bf525967f4a7b735")

---

### Post by renfrew on 2008-05-16
I checked into this more and found that the microdia google group is my next best resource for getting this cam working as this is definitely a microdia cam

Having checked out the links for [https://groups.google.com/group/microdia](https://groups.google.com/group/microdia) I frankly can't figure out how to apply the patch or from where to download said patch. I've only found the .diff file for the patch vs. the original source

I will say that I was able to follow along with everything here: [https://groups.google.com/group/microdia/web/testing-microdia-driver-draft](https://groups.google.com/group/microdia/web/testing-microdia-driver-draft) and got that module installed (cam is recognized as per dmesg) but got no stream whatsoever in camorama or mplayer

I'll be (cross)posting most of this now to the microdia google group as most of my questions now are really specific to their efforts, as far as this thread goes I'd say the issue has been solved...

thanks to milanvora2 and Gunman1982

---

### Post by TonyFordz on 2009-09-23
Does anyone understand those links that this guy posted because I have this same cam & am trying to get it to work with Ubuntu.

---

