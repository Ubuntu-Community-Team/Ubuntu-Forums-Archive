---
title: "Split Screen"
date: 2010-02-11
forum: Multimedia Software
---

### Post by louis.roux on 2010-02-11
I just installed 9.10 on my acer as a second partition.  The only problem I am having is my split screen is not working correctly.  They just mirror each other so I have basically 2 monitors doing exactly the same thing.  No splits.

My graphics card is nvidia geforce 7300 LE

Please help!!

---

### Post by skierkyles on 2010-02-11
Hi,

Have you installed the Nvidia graphics driver yet?

If not, just click this [apt:nvidia-glx-185](apt:nvidia-glx-185), install it, then restart. 

According to this page, that driver should support your graphics card.. 
[http://packages.ubuntu.com/karmic/nvidia-glx-185](http://packages.ubuntu.com/karmic/nvidia-glx-185)



if you have installed the graphics driver, open up a terminal (you will find this in: Applications - Accessories - Terminal), and type in
```

sudo nvidia-settings

```

then click "X Server Display Configuration" 

then click the monitor you want to enable, and click configure,

then check the box for "TwinView" and press "Ok"

then press Apply, if it is working properly, click "Save to X Configuration File" and it will automaticly be enabled from that point on!

---

### Post by louis.roux on 2010-02-11
Done...Thanks

---

