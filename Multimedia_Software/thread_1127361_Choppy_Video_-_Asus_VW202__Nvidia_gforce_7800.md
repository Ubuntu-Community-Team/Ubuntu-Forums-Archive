---
title: "Choppy Video - Asus VW202 / Nvidia gforce 7800"
date: 2009-04-16
forum: Multimedia Software
---

### Post by barney_1 on 2009-04-16
Hi Folks,

I've recently purchased a 22" Asus lcd monitor (ACI VW202).  I'm runnning it from the DVI port of an nvidia gforce 7800 GTX which I had been using for a few years with an analog crt monitor.

I've noticed that when I play video I get a bit of choppiness... as if part of the video is freezing in a horizontal pattern and then tracking upward on the screen.  This behavior is very quick but enough to draw your eye.  I didn't notice this with the analog monitor.  Does anyone know what might be causing this?

I'm driving the monitor at 1280x1050 @ 60hz.  Here is the out put of xrandr:
```
$ xrandr
Screen 0: minimum 320 x 240, current 1680 x 1050, maximum 1680 x 1050
default connected 1680x1050+0+0 0mm x 0mm
   1680x1050      50.0     52.0    108.0* 
   1280x1024      51.0     60.0  
   1600x1024      53.0  
   1440x900       54.0  
   1400x1050      55.0     56.0     57.0  
   1360x768       58.0     59.0  
   1280x960       61.0  
   1152x864       62.0     63.0     64.0     65.0  
   1024x768       66.0     67.0     68.0  
   960x600        69.0  
   960x540        70.0  
   896x672        71.0  
   840x525        72.0     73.0     74.0     75.0  
   832x624        76.0  
   800x600        77.0     78.0     79.0     80.0     81.0     82.0  
   800x512        83.0  
   720x450        84.0  
   680x384        85.0     86.0  
   640x512        87.0     88.0  
   640x480        89.0     90.0     91.0     92.0  
   576x432        93.0     94.0     95.0     96.0  
   512x384        97.0     98.0     99.0  
   416x312       100.0  
   400x300       101.0    102.0    103.0    104.0  
   320x240       105.0    106.0    107.0  

```

Thanks for any help you can give in troubleshooting this problem.

---

### Post by zeex on 2009-04-16
Hi Barney,

To me it seems you have a high resolution LCD screen and with very low refresh rate (1280x1050 @ 60hz). Have you installed the latest nVIDIA drives for your card or you are using the default display driver from ubuntu. 

If you haven't installed the latest driver. I hope installing new driver might solve the issue. You can then increase the refresh rate. 

Also nvidia-setting in ubuntu really helps in changing different setting.

Hemant 
Ubuntu 8.10

---

