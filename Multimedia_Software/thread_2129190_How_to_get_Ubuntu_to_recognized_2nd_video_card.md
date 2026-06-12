---
title: "How to get Ubuntu to recognized 2nd video card"
date: 2013-03-25
forum: Multimedia Software
---

### Post by Webnet on 2013-03-25
So I setup a 2nd video card. I'm currently running a GeForce GTX 460 and added this: [http://www.amazon.com/gp/product/B0049MPQA4/ref=oh_details_o01_s00_i00?ie=UTF8&psc=1](http://www.amazon.com/gp/product/B0049MPQA4/ref=oh_details_o01_s00_i00?ie=UTF8&psc=1) to run a 3rd monitor on. I've booted up my Ubuntu and it doesn't seem to be detecting the additional video card.


It is successfully detected in Windows.


Is there something I need/can do to get Ubuntu to detect it?

---

### Post by Webnet on 2013-03-26
Is there a place where I can go to verify that Ubuntu recognizes that I have 2 video cards connected to my motherboard?

---

### Post by Cheesemill on 2013-03-26
What's the output of...
```
lspci | grep VGA
```

Which graphics driver are you using? The default Ubuntu open source driver or have you installed the closed source Nvidia driver from 'Additional Drivers'.

---

### Post by Webnet on 2013-03-26
```
01:00.0 VGA compatible controller: NVIDIA Corporation GF104 [GeForce GTX 460] (rev a1)
02:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 8400 GS] (rev a2)

```

I'm using the "NVIDIA xorg driver, kernel module and VDPAU library from nvidia-current (proprietary, tested)" from "Additional Drivers"

---

### Post by Webnet on 2013-03-26
There's slightly more detail here: [http://askubuntu.com/questions/272887/what-does-seperate-x-screen-mean-on-my-nvidia-settings](http://askubuntu.com/questions/272887/what-does-seperate-x-screen-mean-on-my-nvidia-settings)

I discovered that if I go to command line and type *nvidia-settings* it'll load the driver settings dialog.

---

### Post by Webnet on 2013-03-26
To get your video cards detected, go to command line and type **nvidia-settings **to load the below dialog

[IMG]http://i.stack.imgur.com/9p8gK.png[/IMG]

---

