---
title: "Extra screen on a Toshiba Tecra M3"
date: 2010-10-08
forum: Multimedia Software
---

### Post by redtop on 2010-10-08
I have a Toshiba Tecra M3 laptop with a resolution of 1024 X 768 and a Nvidia GeForce Go 6600 TE/6200 TE graphics adapter build in, on to which I want to add an external Dell E196FP monitor with a resolution of 1280 X 1024 pixels.

I have installed the Nvidia VIDIA UNIX x86 Kernel Module  173.14.22 driver and X server application, but when I go in to the application by "System" -> "Monitors" I get the following message: "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?", to which I answer yes!

In here, I go to "X Server display configuration", and "Detect displays".

Here both displays (the Dell and the build-in Toshiba) is shown, but I do not know what setting to chose under "Configure", where I have 3 options:
[LIST]
[*]Disabled
[*]Separate X screen
[*]TwinView
[/LIST]

I want the same screen image on both displays - almost like a projector, but I can for the life of me not get it to work!

What am I doing wrong?

Am I doing it all wrong?

I am very new to Linux, and when I had Windows installed on the Toshiba, I just pressed [Fn]+[F5]!

---

### Post by gordintoronto on 2010-10-08
You want Twinview.

You have installed a very old video driver. How?

What version of Ubuntu are you using?

The Geforce 6600 is also quite old.  Perhaps you would be better off with the non-proprietary driver.

---

