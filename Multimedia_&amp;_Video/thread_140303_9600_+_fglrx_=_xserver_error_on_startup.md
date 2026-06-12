---
title: "9600 + fglrx = xserver error on startup"
date: 2006-03-05
forum: Multimedia &amp; Video
---

### Post by Compton on 2006-03-05
i am sure this has been covered a dozen times but....

i have no problems with ATI drivers after configuring the driver, but if i choose fglrx (like EVERY guide tells me to) i cannot get gnome to run on startup.

i think one of the last lines i get for the error says unidentified hardware on bus id 1:0:1 

i am not sure where i am going wrong here. after i get the xserver error i tried fglrxinfo  and it says i am still using mesa.

any simple fixes?

if you need more info tell me what files to post....

---

### Post by anirban.sam on 2006-03-05
sudo dpkg-reconfigure xserver-xorg

---

### Post by Compton on 2006-03-05
right, and then I get the error when i restart with fglrx.

if i reconfigure and choose ATI, i get no graphics acceleration.

how can i get this to work with the good driver.

---

