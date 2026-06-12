---
title: "ZC0302 Webcam Gray Image in Camorama"
date: 2008-07-25
forum: Multimedia Software
---

### Post by gborges911 on 2008-07-25
Hello to everyone, I'm kinda new in all this linux stuff, I just installed kubuntu hardy and I like it a lot. I am very happy with kubuntu but I still can't put my webcam to work.
My webcam is an USB webcam with a mic integrated (ZC0302), I installed the gspca drivers using easycam2, the system recognizes my webcam, and the integrated mic works perfectly, when I run camorama, the green led inside the cam turns on, but I get a fully gray image!...
I really appreciate your help, the webcam is the only thing that ties me to windows right now, so as I said before i really appreciate your help!...
I will attach here some info that I think may be useful...

```

gonzalo@lenovo:~$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0ac8:0302 Z-Star Microelectronics Corp. ZC0302 WebCam
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems)
Bus 001 Device 001: ID 0000:0000
```

```
gonzalo@lenovo:~$ ls /dev/video*
/dev/video0
```

```
gonzalo@lenovo:~$ dmesg | grep gspca
[   29.134724] /usr/share/EasyCam2/drivers/gspca/gspca_core.c: USB GSPCA camera found.(ZC3XX)
[   29.134731] /usr/share/EasyCam2/drivers/gspca/gspca_core.c: [spca5xx_probe:4280] Camera type JPEG
[   30.052503] /usr/share/EasyCam2/drivers/gspca/Vimicro/zc3xx.h: [zc3xx_config:597]  Sensor UNKNOW_0 force Tas5130
[   30.058496] /usr/share/EasyCam2/drivers/gspca/gspca_core.c: [spca5xx_getcapability:1254] maxw 640 maxh 480 minw 160 minh 120
[   30.058548] /usr/share/EasyCam2/drivers/gspca/gspca_core.c: data format set to RGB
[   30.058589] usbcore: registered new interface driver gspca
[   30.058593] /usr/share/EasyCam2/drivers/gspca/gspca_core.c: gspca driver 01.00.20 registered
[   76.650156] /usr/share/EasyCam2/drivers/gspca/gspca_core.c: [gspca_set_isoc_ep:950] ISO EndPoint found 0x81 AlternateSet 7
[  258.651811] /usr/share/EasyCam2/drivers/gspca/gspca_core.c: [gspca_set_isoc_ep:950] ISO EndPoint found 0x81 AlternateSet 7
[  290.965343] /usr/share/EasyCam2/drivers/gspca/gspca_core.c: [gspca_set_isoc_ep:950] ISO EndPoint found 0x81 AlternateSet 7
```

If you need any additional information please just let me know, and thanks!... (and sorry for my bad English)

---

