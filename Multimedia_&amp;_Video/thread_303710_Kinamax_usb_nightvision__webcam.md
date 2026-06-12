---
title: "Kinamax usb nightvision  webcam ?"
date: 2006-11-20
forum: Multimedia &amp; Video
---

### Post by mikq on 2006-11-20
I'm new to linux and looking for a webcam to video conference with my daughter across country, she uses windows !! But I use Ubuntu and was wondering if the Kinamax usb nightvision webcam will work with ubuntu.. Any feedback or advice would be greatly appreciated

Thanx

---

### Post by beckster on 2006-12-20
I'm wondering the same thing.

---

### Post by jglepage on 2007-12-06
I just got a new  KINAMAX WCM-6LNV Webcam (0.35MP Effective Pixels 640 x 480 30fps USB Interface).  $20 including shipping at newegg.com.

It works on Linux.  Hooray.  The LED's don't seem to come on until it's completely dark, but that's easily fixed: just cover the light sensor on the top of the camera.

No visible light coming from the LED's.

This is what caminfo said about the camera:
Device node      : /dev/video1
Name of device   : "Generic Zc0305b"
Minimum size     : 176x144
Current size     : 0x0
Maximum size     : 640x480
Video inputs     : 1
 Input 0
  Name             : "ZC301-2"
  Type             : Camera
  Audio            : no
  Tuners           : 0
Audio inputs     : 0


I'm running Edubuntu 7.04

---

### Post by jimmyridge on 2008-02-08
nice hardware but a bit slow i think you only get 15fps in 640x480 mode and 30fps in 320x240 :P   hey for 15$ what do you expect?  i plan i mouting em outdoors soon (weather gets a bit better) i have this old crumby p2 @200 or so mhz be perfect for dumping video with motion video for linux progy

UDATE: i've since upgraded to hardy but sofar it doesnt autodetect it and work (no /dev/video0 device) <work in progress>

UPDATE 2 : ok found the driver/module it uses via googling newegg comments rock "The v4l driver module you will need is either the spca5xx or the newer gspca module."  i'm downloading the gspca module  catting the README i knotice this

lsusb says ID 0ac8:305b Z-Star Microelectronics Corp. ZC0305 WebCam

grep of README 
james@Acer-4315:~/sandbox/gspcav1-20071224$ cat READ_AND_INSTALL |grep  micro
manufactured by SunPlus Sonix Z-star Vimicro Conexant Etoms Transvision Mars-Semi Pixart
    {USB_DEVICE(0x0ac8, 0x301b)},	/* Asam Vimicro */
    {USB_DEVICE(0x0ac8, 0x0302)},	/* Z-star Vimicro zc0302 */
    {USB_DEVICE(0x0ac8, 0x305b)},	/* Z-star Vimicro zc0305b */
    {USB_DEVICE(0x0ac8, 0x303b)},	/* Vimicro 0x303b */
A note on Sunplus Z-star Vimicro Conexant Transvision Etoms Pixart Mars-Semi and our interaction with them so far
james@Acer-4315:~/sandbox/gspcav1-20071224$ 

so i'm sure it'll work  and yupers like a charm  cheers!

---

