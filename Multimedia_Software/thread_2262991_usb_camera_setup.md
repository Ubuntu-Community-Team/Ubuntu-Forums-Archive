---
title: "usb camera setup"
date: 2015-01-28
forum: Multimedia Software
---

### Post by jgw on 2015-01-28
I am running with ubuntu 14.10 and have a logitech usb camera plugged in.  I checked to see if the system recognized the camera and it did:
Bus 001 Device 008: ID 046d:0829 Logitech, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x046d Logitech, Inc.
  idProduct          0x0829 
  bcdDevice           28.a6
  iManufacturer           1  
  iProduct                2 Webcam C110
  iSerial                 0 
  bNumConfigurations      1

I then tried to access this camera with "Camera".  This is a strange program in that there is no documentation or buttons to push, etc.  It did light up with the camera output, however, 1 time.  That program also kept quitting all on its own so I moved onto Cheese.  This seems to be a good way to go but it tells me that the GLstreamer module is missing something called cluttervideosink.  I then went to synaptic to find this - no cigar.  I also searched and found that somebody else had this problem but never got the problem solved as far as I could tell.

When I run Cheese a light, on the front of the camera goes on, then off, and cheese tells me there was an error whilst playing video.  After a while it then tells me there is no device.  I then tried guvcview.  I click on it and then it stops and tells me there was an error and send the report.  I used to be able to see something but, now, nothing.  I have also uninstalled cheese and reinstalled (made no difference).  The camera is a logitech c110 which is in the list of valid cameras for ubuntu.  

I just swapped out the c110 for a Cubeternet GL-UPC822 UVC WebCam (as per lsusb).  Now cheese works and so does camera.  The picture is not good and the video is also not good but at least I have a picture.  more work, I fear, I am going to mark this one as solved.

Does anybody know how one is supposed to hook up a camera.  I, obviously, have no clue.

Thank you...........

---

