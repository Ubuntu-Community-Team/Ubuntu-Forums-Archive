---
title: "Hercules Classic Silver Webcam"
date: 2008-07-02
forum: Multimedia Software
---

### Post by TenienteCastillo on 2008-07-02
Hello, I've just bought a really cheap webcam, Hercules Classic Silver, and I've been 3 days searching and trying to configure it.

My best is to compile & install gspca driver and then, Cheese keeps looking for a devide and Camorama hangs showing the name of the cam in the title bar.

Last lines of dmesg:

```
[ 2057.903852] /home/jbernal/webcam/gspcav1-20071224/gspca_core.c: [spcaDetectCamera:4255] Hercules Classic Silver Mod By Sebtx :)
[ 2057.903857] /home/jbernal/webcam/gspcav1-20071224/gspca_core.c: USB GSPCA camera found. SONIX JPEG (sn9c1xx) 
[ 2057.903860] /home/jbernal/webcam/gspcav1-20071224/gspca_core.c: [spca5xx_probe:4303] Camera type JPEG 
[ 2057.905858] /home/jbernal/webcam/gspcav1-20071224/gspca_core.c: [spca5xx_getcapability:1258] maxw 640 maxh 480 minw 160 minh 120
[ 2057.905908] usbcore: registered new interface driver gspca
[ 2057.905912] /home/jbernal/webcam/gspcav1-20071224/gspca_core.c: gspca driver 01.00.20 registered
[ 2057.951772] /home/jbernal/webcam/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:953] ISO EndPoint found 0x81 AlternateSet 8
[ 2071.331827] /home/jbernal/webcam/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:953] ISO EndPoint found 0x81 AlternateSet 8
[ 2071.913319] /home/jbernal/webcam/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:953] ISO EndPoint found 0x81 AlternateSet 8
[ 2072.447001] /home/jbernal/webcam/gspcav1-20071224/gspca_core.c: [spca5xx_do_ioctl:2133] Bridge SN9CXXX 
[ 2072.447032] /home/jbernal/webcam/gspcav1-20071224/gspca_core.c: [spca5xx_do_ioctl:2133] Bridge SN9CXXX 
[ 2072.447245] /home/jbernal/webcam/gspcav1-20071224/gspca_core.c: VIDIOCMCAPTURE: invalid format (7)
[ 2091.297705] /home/jbernal/webcam/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:953] ISO EndPoint found 0x81 AlternateSet 8
[ 2091.843169] /home/jbernal/webcam/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:953] ISO EndPoint found 0x81 AlternateSet 8

```

lsusb:
```
Bus 002 Device 004: ID 06f8:3004 Guillemot Corp.
```

Any help would be veri appreciated. (Sorry for my english).
Thanks a lot.

---

### Post by linuxwizard on 2008-07-02
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by TenienteCastillo on 2008-07-03
Opening Ekiga shows the error message saying that it cannot open /dev/.static/dev/video0 although the node exists:

```

$ ls -l /dev/.static/dev/video0 
crw-rw---- 1 root video 81, 0 2008-06-28 20:17 /dev/.static/dev/video0
```

And my user is in group video, so I have the right permissions.

When I open Ekiga after the wizard selecting V4L2 and device /dev/.static/dev/video0 it shows the same message again, saying that it will transmit the logo animation instead of the camera image.

---

### Post by linuxwizard on 2008-07-03
From what I found searching you are using wrong driver. Looks like from here > [http://alpha.dyndns.org/ov511/cameras.html](http://alpha.dyndns.org/ov511/cameras.html) > you need the OV518. Untested on your webcam may not work. I did a Google search on > Bus 002 Device 004: ID 06f8:3004 Guillemot Corp > I had to translate a few links but it looks like others are having issues trying to get the webcam to work.

---

### Post by TenienteCastillo on 2008-07-05
Thank you, but I've tested the OV518 and It does not work. It works with another version of the same camera as seen in the forums, but it doesn't work with the Guillemot chips.

---

### Post by jai_mantravadi on 2008-08-21
Did you try the UVC drivers? I can't seem to get it to work with my system, but if my research was able to help you, then it would be great. 

A USB id just 1 off your hercules was listed here: [http://linux-uvc.berlios.de/]("http://linux-uvc.berlios.de/")

The id is 06f8:3005 vs 06f8:3004 for our camera. Maybe you just need to do a sudo depmod and sudo modprobe uvcvideo? from dmesg, I get 
```

[163902.119650] Linux video capture interface: v2.00
[163902.161140] usbcore: registered new interface driver uvcvideo
[163902.161145] USB Video Class driver (SVN r244)

```

lsusb -vd 06f8:3004 yeilds the output (in file) for me. I got an error at the end that said "cannot read device status, Operation not permitted (1)"

I'd be interested in getting this webcam working in linux if anyone else has it and can help debug. Thanks!

---

### Post by pavel989 on 2008-09-28
so do u techincally have it running? i havent gottena chance to try it on my linux boot yet, guess i can do that and help yall out

---

