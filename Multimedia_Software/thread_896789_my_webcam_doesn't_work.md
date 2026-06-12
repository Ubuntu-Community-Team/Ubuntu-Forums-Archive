---
title: "my webcam doesn't work"
date: 2008-08-21
forum: Multimedia Software
---

### Post by agf.1000 on 2008-08-21
I have bought a webcam and when I tried to use it on **ubuntu** it doesn't work...
When I used **lsusb** command I've got this
```
...  

Bus 001 Device 002: ID 0ac8:307b Z-Star Microelectronics Corp. 

... 
```


can any one help me with this issue please!!! :mad:

---

### Post by linuxwizard on 2008-08-21
Try using Ekiga see if the webcam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by agf.1000 on 2008-08-22
I only see the bouncing logo, and every thing related to video settings responds very slowly

I found this [blog]("http://quilombo.wordpress.com/2008/02/02/zaapa-webcam-en-ubuntu-linux-710-gutsy-gibbon-2/") talking about the same problem
and I tried to implement the steps but I still have no video display from my webcam.

---

### Post by linuxwizard on 2008-08-22
You need the gspca driver.
[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

This is for Gusty how to install I don't think this will work on Hardy.
[http://quilombo.wordpress.com/2008/02/02/zaapa-webcam-en-ubuntu-linux-710-gutsy-gibbon-2/](http://quilombo.wordpress.com/2008/02/02/zaapa-webcam-en-ubuntu-linux-710-gutsy-gibbon-2/)

Also if you do a search in the forum you will notice that alot of people have had issues trying to make that webcam work.

---

