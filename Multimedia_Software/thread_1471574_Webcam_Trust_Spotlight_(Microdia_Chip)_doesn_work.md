---
title: "Webcam Trust Spotlight (Microdia Chip) doesn work"
date: 2010-05-03
forum: Multimedia Software
---

### Post by Bergfex on 2010-05-03
Hello.

Maybe someone of you can help me. On the German Ubuntu-forum people unfortunately could not solve my problem. I want to get run my webcam (a Trust Spotlight / no Spotlight Pro). This webcam has a Microdia chip (0c45:6310). Unfortunately the webcam only show a black picture with using video. Taking photos works with Cheese. Very interesting is that I have also tried Ubuntu 09.04 via Live-CD and with this Ubuntu-version the webcam works perfectly. So it must be possible. Please help me with installing the correct driver. Thanks a lot. Bergfex.

---

### Post by no2498 on 2010-05-04
in cheese go to edit preferences set the resolution lower
to a small number

hope this helps

---

### Post by intel on 2010-05-05
find out the bridge controller & sensor used, most probably you are using the gspca kernel driver, else you have the UVC driver.

---

### Post by Bergfex on 2010-05-06
> **intel said:**
> find out the bridge controller & sensor used, most probably you are using the gspca kernel driver, else you have the UVC driver.

Please can you tell me, hoe I can find out this. In skype I don't get any picture (only black). Thanks.

---

### Post by no2498 on 2010-05-07
open a terminal type, lsusb click enter

copy and paste it here

---

### Post by Bergfex on 2010-05-09
> **no2498 said:**
> open a terminal type, lsusb click enter

copy and paste it here

```
Bus 003 Device 007: ID 043d:00ff Lexmark International, Inc. InkJet Color Printer
Bus 003 Device 006: ID 043d:007d Lexmark International, Inc. Photo 3150
Bus 003 Device 004: ID 049f:000e Compaq Computer Corp. Internet Keyboard
Bus 003 Device 003: ID 043d:007a Lexmark International, Inc. Generic Hub
Bus 003 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Hama Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:6310 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Here you are. It's the Microdia chip.

---

### Post by no2498 on 2010-05-09
is the cam plugged in to a usb port hub ?
plug it in to the computer its self

this is not for skype

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

910 and up cheese is loaded
look in sound&video cheese webcam booth

see if the cam works in it

---

### Post by Bergfex on 2010-05-10
I have now entered the gestreamer-properties. Then a grafic comes where i can test audio and video. In the test the webcam works with v4l2. Interesting is that it works much better than in cheese. In cheese the pictures changes every three seconds; In the test the video works much more fluently.

---

### Post by no2498 on 2010-05-10
read and install what the page tell you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

it works better for me

i hope you can get it loaded

glad you got the cam working some is better than none lol

---

### Post by Bergfex on 2010-05-10
Hello No2498

thanks for your help. With WXCam (I haven't known this programma) the wabcam works perfectly. Much better than in Cheese.

Greets.

---

### Post by no2498 on 2010-05-10
your welcomw

edit your first post to read

solved Webcam Trust Spotlight (Microdia Chip) doesn work

---

