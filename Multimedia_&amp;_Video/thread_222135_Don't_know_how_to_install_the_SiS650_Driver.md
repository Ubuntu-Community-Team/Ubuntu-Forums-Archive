---
title: "Don't know how to install the SiS650 Driver"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by eshed on 2006-07-24
[I use Ubuntu 6.06 Dapper Drake]

I found and downloaded the SiS650 driver (sis_drv.so), but I don't know how to install it. I saw somewhere these instructions and followed them, but it didn't work, sadly:

I used the kernal without the GUI, and typed:

sudo /etc/init.d/gdm stop
sudo cp sis_drv.so /usr/lib/xorg/modules/drivers
sudo cp sis_drv.so /usr/X11R6/lib/modules/drivers
sudo /etc/init.d/gdm start

NOTE: the two folders to which I copied the file were displayed in the guide, so I copied the file to both of them, just to make sure :).

After that the login GUI comes back, and when I login it's as if I did nothing ](*,). The screen refresh rate is still low, the 3d stuff are poorly displayed and are run so sloooow.

For instance, the earth in Google Earth for Linux is barely moving...  
In Windows it moved really good. So I'm sure my poor graphics card supports that ;) 

...any suggestions? :-\

Regards,
eshed

---

### Post by hil on 2006-07-24
Can you try to load the vesa driver for your sis video chip. I had a sis650 on a laptop. I had to use vesa driver although I was using Mandrake. There should be a way to install vesa driver in ubuntu and tell X to use it. You might dig into that.

---

