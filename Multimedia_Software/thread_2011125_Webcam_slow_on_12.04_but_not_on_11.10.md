---
title: "Webcam slow on 12.04 but not on 11.10"
date: 2012-06-26
forum: Multimedia Software
---

### Post by nourathar on 2012-06-26
Hello,

after experimenting with a very cheap webcam I recently bought a Logitech C310 for a project.
On my Alienware m11xr2 laptop under Ubuntu 11.10 it runs great: 30fps of 640x480, no problem when I run guvcview (after setting the exposure to manual, that is).
On my desktop (self-assembled with an Asus P8Z68-M PRO board, an i7-4core and an NVIDIA gx580 card) under Kubuntu 12.04 to my big surprise it maxes out at exaclty 16fps, whatever I try: also smaller resolutions, all format options, I tried all the controls I could find, but no difference.

I am very much surprised by this, since I built my desktop system to be fast. I can think of two explanations, but I have no idea if they make sense and how I can resolve this:

- is there some kind of regression in the newer kernel that is used in 12.04 ? very unlikely ?

- could it be that I have slow usb-controller or that usb is not working on its full speed ? How can I check or set this ? The motherboard only has usb 2.0 or 3.0 connections it says in the specs and i tried them both with no difference.

or if there are other plausible explanations I would be very curious to hear them. Kind regards,

Joost.

---

### Post by nourathar on 2012-06-26
found out that 
sudo cat /sys/bus/usb/devices/usb?/speed
gives the speed of the usb ports:
on my laptop it is 480 only (usb2),
on my desktop it is 480 and 5000 (usb2 and 3).
But i'm not sure whether these numbers exclude the possibillity of the usb controller being the bottleneck.

---

### Post by nourathar on 2012-06-27
ok, I found a fix but I do not understand what it does:
In the BIOS I enabled the 'EHCI handoff' setting.
Now it runs smoothly with no problems, but I have no idea what I just did..

---

