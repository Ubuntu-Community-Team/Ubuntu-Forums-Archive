---
title: "Low Performance Playing HD Content"
date: 2010-12-06
forum: Multimedia Software
---

### Post by vlamnire on 2010-12-06
My friend has a Dell Inspiron 4600 desktop that we recently install Ubuntu on to replace Windows XP on.  Now when we try to play some HD videos in VLC player it's pretty low frame rate but I'm not sure why.  If we play 720p on YouTube it's pretty low frame rate too.

In Windows XP he could play these videos flawlessly.  We tried installing a NVIDIA driver but it stops the desktop from working.  In 10.04 the driver installed fine, however, in 10.10 after installing the driver on next boot it would start up at just a terminal.  Not a terminal window but just a black screen with white text on the entire monitor.  I could only fix it by editing the xorg.conf changing a field that said "Device: Nvidia" to "Device: nv".  That driver may also be causing a problem.  

If I cannot find a solution we will reinstall Windows XP which I rather not do because I think Ubuntu runs better.  Also, we installed xubuntu-desktop package so we are running XFCE instead of GNOME.

---

### Post by vlamnire on 2010-12-07
Surely there must be a solution besides dealing with it because the PC is to slow.

---

### Post by inobe on 2010-12-07
the best advice i can give, i have a low resource pentium system that has an agp slot, i installed an pny fx5200 ultra because the onboard video sucked at best, vendors haven't released good enough legacy drivers for linux, in fact these drivers are already forgotten about which leaves the opensource 2d nvidia drivers.

you can still find nvidia agp cards, models up to 6200 le's or older more powerful nvidia 7800gs cards on ebay.

on another old system i swapped the motherboard and made that old pentium relic a beast without having to buy another processor, you can move from agp to pci-e and install an awesome video card, move from plain ddr to ddr2, 1gb stick of ddr2 memory is only 14 dollars, move from slow ide hard drive interface to sata disk speeds, you can grab a 1tb sata hard drive for 49 dolars.

a huge upgrade with very little cash.

if you go that route it wouldn't matter what os you installed, it'll perform.

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007627%20600007878&IsNodeId=1&name=478](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007627%20600007878&IsNodeId=1&name=478)

---

### Post by tommcd on 2010-12-07
> **vlamnire said:**
> ... We tried installing a NVIDIA driver but it stops the desktop from working.  In 10.04 the driver installed fine, however, in 10.10 after installing the driver on next boot it would start up at just a terminal. ...
Perhaps you could start by telling us:
1. What nvidia card is in the computer?
2. How did you install the nvidia driver? Did you install the driver from the Ubuntu repos? If so, then which one? Or did you install the driver from nvidia.com? If so, then how did you install it?
The more detailed questions generally get the best answers.

As for flash, the proprietary flash player from Adobe does have high CPU usage in linux. This is because Adobe does not put as much effort into developing their linux flash player as they do their Windows flash player.
The new flash 10.2 beta does bring hardware acceleration to linux though:
[http://www.phoronix.com/scan.php?page=news_item&px=ODg1Mg](http://www.phoronix.com/scan.php?page=news_item&px=ODg1Mg)
This does require that you have a good enough video card to support hardware acceleration though.  
I am using the 10.2 beta in Slackware. High def 720p videos on YouTube seem to play a bit better since I installed this. I have not had any problems with flash 10.2 beta so far.

---

### Post by vlamnire on 2010-12-11
[QUOTE=tommcd;10213175]Perhaps you could start by telling us:
1. What nvidia card is in the computer?
2. How did you install the nvidia driver? Did you install the driver from the Ubuntu repos? If so, then which one? Or did you install the driver from nvidia.com? If so, then how did you install it?
The more detailed questions generally get the best answers.

I think it's a NVIDIA FX5200 and I installed the driver by going to System > Administration > Hardware Drivers

If I install it now though it won't load the desktop just a full screen terminal.  It did install properly in 10.04, I did not test video playback in 10.04 however.

---

### Post by tommcd on 2010-12-11
> **vlamnire said:**
> 
I think it's a NVIDIA FX5200 and I installed the driver by going to System > Administration > Hardware Drivers

To verify that it is a nvidia fx5200, open a terminal and post the output of:
```
lspci | grep -i vga
```
For the nvidia 5200 you should have the nvidia-173 driver installed from the Ubutnu repos.
[http://packages.ubuntu.com/maverick/nvidia-173](http://packages.ubuntu.com/maverick/nvidia-173)
 When you look in System > Administration > Hardware Drivers, does it show you the nvidia-173 driver is enabled?
Post the output of: ```
glxinfo | grep -i render
``` to verify that the nvidia driver is enabled. It should report something like:
```

bash-4.1$ glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: GeForce 8400 GS/PCI/SSE2/3DNOW!
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info,

```
EDIT: You need to install the **mesa-utils** package to run glxinfo.

---

### Post by ShadowTek on 2010-12-11
Disable compiz while watching videos, which should help some.
```

alt+F2
metacity --replace
```

To switch back:
```
alt+F2
compiz --replace
```

Edit: Oh, I see you're using xubuntu-desktop.

An xubuntu prefix for the thread title might be more appropriate.

---

### Post by vlamnire on 2010-12-12
> **tommcd said:**
> To verify that it is a nvidia fx5200, open a terminal and post the output of:
```
lspci | grep -i vga
```
For the nvidia 5200 you should have the nvidia-173 driver installed from the Ubutnu repos.
[http://packages.ubuntu.com/maverick/nvidia-173](http://packages.ubuntu.com/maverick/nvidia-173)
 When you look in System > Administration > Hardware Drivers, does it show you the nvidia-173 driver is enabled?
Post the output of: ```
glxinfo | grep -i render
``` to verify that the nvidia driver is enabled. It should report something like:
```

bash-4.1$ glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: GeForce 8400 GS/PCI/SSE2/3DNOW!
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info,

```
EDIT: You need to install the **mesa-utils** package to run glxinfo.

The problem is that when I activate the driver on next boot it just shows a screen that says the name of the computer like

jordan-desktop login: _ 

With the underscore blinking of course so it's a dilemma here.  I can post the output of those commands later.

I left the driver enabled and upgraded to 10.10 from the Software Update and when I rebooted I got that screen and I fixed it by editing the xorg.conf with nano and the desktop loaded.  Maybe the old driver installation left stuff behind that is incompatible with 10.10?

---

### Post by tommcd on 2010-12-12
> **vlamnire said:**
> 
I left the driver enabled and upgraded to 10.10 from the Software Update and when I rebooted I got that screen and I fixed it by editing the xorg.conf with nano and the desktop loaded.  Maybe the old driver installation left stuff behind that is incompatible with 10.10?
So what driver do you have listed in xorg.conf when you can boot to the desktop? Is it "nv" or "nvidia"?
After enabling the nvidia driver, it should be "nvidia".

---

### Post by vlamnire on 2010-12-13
> **tommcd said:**
> So what driver do you have listed in xorg.conf when you can boot to the desktop? Is it "nv" or "nvidia"?
After enabling the nvidia driver, it should be "nvidia".

It's nv.  It's the only way I could get to the desktop.  I used nano to edit it then restarted and I got the desktop back.

What I'm wondering is if there is a way to completely remove nvidia driver and re-enable it.  If there is, will that solve video playback issue?

---

### Post by ShadowTek on 2010-12-13
> The problem is that when I activate the driver on next boot it just shows a screen that says the name of the computer like

jordan-desktop login: _ 

> **vlamnire said:**
> It's nv.  It's the only way I could get to the desktop.

If you don't know how to get to desktop manually, all you have to do is enter your username at the "login" promt, then enter your password, then type **startx** and hit enter.

---

