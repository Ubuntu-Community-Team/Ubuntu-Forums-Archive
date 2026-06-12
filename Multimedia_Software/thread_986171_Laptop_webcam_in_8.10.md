---
title: "Laptop webcam in 8.10"
date: 2008-11-18
forum: Multimedia Software
---

### Post by FizzBuntu on 2008-11-18
Hi there
I convinced my father to use ubuntu and so fare things are going OK.
Now that the basics are working, I'd like to make the reste of it work too, the webcam.
So far I've read a lot of posts about different kind of webcam using differnet drivers and modules and apps, but so far, nothing worked.
What informations would be required to clearly identifie the model and brand of the webcam ?
And then I can hope to find some answers.

---

### Post by FizzBuntu on 2008-11-20
up !!

---

### Post by vanquishedangel on 2008-11-22
I will copy and paste the solution I found here
hope it helps

I hope this is not too late but I have been tirelessly looking to get my webcam to work in ubuntu intrepid 8.10 to the point of pulling my hair out but I didn't give up and if this doesn't help you then maybe it will help someone like me but I found this on another web page and compiled it from others and it worked like a dream, I will copy and paste the article

The only way I have managed to make totem show the videos was to set the output on the video tab of gstreamer-properties to "X Window System (No Xv)".

How to change the properties in gstreamer: press alt, f2. Then type gstreamer-properties, then go to the video tab and under default imput change the plugin to "x window system ( no xv)" Now start cheese.
vanquishedangel is online now Report Post   	Edit/Delete Message

---

### Post by forkandles on 2008-11-23
Go to the terminal and type  lsusb

This will give you manufacturer and product ID codes for the built-in webcam.
I should warn you that laptop built-in webcams often do not work in Linux.
There is enough of a problem trying to get aftermarket designed-for-Windows webcams working in Linux.

You could have a look here to see if your webcam is mentioned:
[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

To give you an idea of the scale of the webcam in Linux problem look here (I won eventually):
[http://ubuntuforums.org/showthread.php?t=990057&highlight=experiences+8.10+skype+vision+pro](http://ubuntuforums.org/showthread.php?t=990057&highlight=experiences+8.10+skype+vision+pro)

Just to cheer you up a bit, here is a review of a Dell Vostro 1710 where everything appears to work perfectly, including the webcam. 
In this case lsusb shows device 004 to be a Microdia with codes 0c45:63e0

[http://blog.ptpbs.com/?p=37](http://blog.ptpbs.com/?p=37)

Good luck.

---

### Post by FizzBuntu on 2008-11-30
well the lsusb command gave me
Bus 006 Device 003: ID 0402:5602 ALi Corp. Video Camera Controller

and so far I haven't been able to make it work...

any clues ?!

---

### Post by forkandles on 2008-12-01
FizzBuntu,
I may have an early Christmas present for you, but don't get carried away too soon since I suspect that you will also have to put in quite a bit of hard work.
Try this for size.

[http://ubuntuforums.org/showpost.php?p=5055135&postcount=6](http://ubuntuforums.org/showpost.php?p=5055135&postcount=6)

---

