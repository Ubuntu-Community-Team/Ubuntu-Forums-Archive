---
title: "nned help with Samsung U10 FlashCam"
date: 2010-03-04
forum: Multimedia Software
---

### Post by PeteUplink on 2010-03-04
I've just connected my Samsung U10 FlashCam to my laptop and I thought it would have been recognised as a removable HD like my other digital cam. However, nothing shows up at all.

The FlashCam recognises that it's connected to a USB port, and it starts to charge itself from the USB as it would under windows, but it never shows up as a device like it does under windows.

Does anyone know if it's possible for me to access it through Linux?

---

### Post by no2498 on 2010-03-04
if this is a webcam it will not show up like you are thinking
you need a program to see it on/in 910 and up i think cheese is installed
i like wxcam myself you can get it from getdeb or [http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/) read what they say to install first they have a deb file also

ok open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2 click the bottom test button for each 1
if you get any high cpu or memory usage high heat from the fans
do the (  gstreamer-properties ) 1 more time but change the plugin to ,
x window system (no xv) restart the computer
hope this helps

---

### Post by PeteUplink on 2010-03-05
It's a digital camcorder. I guess I should have mentioned that. 

Under windows the U10 shows up as a removable media and recognises it's connected to USB and starts to charge its battery from the USB port. It'll then load up a suite of software that's installed on the camcorder itself so that I can edit video, save pictures and so on.

Under Ubuntu it recognises that it's connected to USB and even starts to charge its battery from the USB port, but I cannot access it as removable media through Ubuntu. The built in software doesn't load either, but I wasn't expecting it to as it's a windows application.

I've tried a lot of different things but Linux just refuses to see the U10 as a removable drive.

I think what I'll have to do is go out and buy a flash card reader, take the card out of the camcorder and access the videos that way.

---

### Post by no2498 on 2010-03-05
it should come up in fspot
plug it in then turn it on see what that brings up for you
if that dose not do any good take the card out an try again

---

### Post by Zerhash on 2010-07-05
i just got a u10

it works fine as is. I havent been on ubuntu in ages. I was able to mount it from my /dev/sd* by plugging it in and turning it on.

If you dont turn it on it will only charge.

good luck

---

