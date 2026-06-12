---
title: "webcam light stays on with ubuntu 9.04"
date: 2009-04-27
forum: Multimedia Software
---

### Post by odysseus7m on 2009-04-27
can anyone please help me.  i recently upgraded to 9.04 and i am annoyed by the fact that the webcam light stays on everytime i boot the computer. i have no programs accessing the webcam and i didnt have this problem with hardy heron. the webcam just powers itself on at startup and doesnt shut off. the webcam seems to be functioning. i tested it with cheese (the image is inverted but thats another issue). does anyone know of a way to turn off the webcam? any help will be greatly appreciated.

alienware m9700
built in bison webcam
2 gigs of ram
1.4 ghz processor
80 gig hard drive.

---

### Post by odysseus7m on 2009-04-27
i forgot to post this

Bus 001 Device 003: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by matrixte on 2009-04-27
hi,
i have the same problem. i'm new in the linux world i like it and i try to learn more about it.

---

### Post by exorcism on 2009-04-28
same problem with me

I also can't seem to get it to work. with cheese i just get a black screen, and when i try to test the video device in skype, i just get a green screen. any ideas? 

here is the output to lsusb:

```
Bus 001 Device 002: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by odysseus7m on 2009-04-28
do you guys have this problem with the 9.04 upgrade or with a fresh install? i had the problem after the upgrade.

---

### Post by odysseus7m on 2009-04-28
i guess i found a work around. i dont know why i didnt think of this before. i use Fn + F4 on my keyboard to turn off/ or turn on the webcam (the function key maybe different on other keyboards) when i run cheese the camera turns on by itself. when i close cheese the camera still stays on but atleast i can turn it off with the function key. my only problem now i guess is how to invert the image.

---

### Post by exorcism on 2009-04-28
it happened both on upgrade and fresh install..

i did a fresh install because of my ati card not being supported anymore by fglrx stuff and  i messed up the display

you say the display is flipped... did you try that with cheese? maybe if you clicked on the effects button from cheese, maybe invert image is selected or smth.

update: webcam works now, don't know why :)) still not on skype though... light is still on :) anyone knows how to shut it down?

---

### Post by odysseus7m on 2009-04-30
hey effects option with cheese worked :) thanks, i didnt know that option was there. camera light still stays on, but atleast i can manually turn it off with the function key

---

### Post by Guell on 2009-05-03
same here after upgrade:
finally my webcam works (built-in, lenovo 3000 v100), but the light is on right after boot and stays on all the time.

---

### Post by ignatzquiron on 2009-05-04
HI! Lenovo 3000 n200, same problem. chess show me good image but grayscale.  I cant turn it off.

---

### Post by efes50cl on 2009-07-01
I have the same problem. My web cam light stays on...And in "cheese" it shows black and white. Does anyone know the function key short cut to close the cam for 
Lenovo 3000 V200 ?
My Ubuntu is Notebook Remix"" 9.4

---

### Post by Kinnza on 2009-07-25
im having the same problem
cam light stays on (and it seems like the cam is just always on)
i dont think i have a fn key that shuts it so basicly im a bit paranoid here that cam is alway on... haha

also image is in black and white

cheese is set to no-effect. and i also tried to change some of em but it doesnt change much colorwise.

any ideas?

---

### Post by no2498 on 2009-09-08
just a note
usb
has power all the time

---

