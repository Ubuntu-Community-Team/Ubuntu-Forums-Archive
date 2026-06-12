---
title: "Teac Mx-4 webcam on ubuntu"
date: 2008-08-16
forum: Multimedia Software
---

### Post by java.jfan on 2008-08-16
Hi, Recently I've got Teac Webcam Mx-4 1.3M Webcam.
While it works perfectly on windows XP, I can't get it work on the Ubuntu on the same machine. I'm using an up-to-date latest version of ubuntu 8.04.
I would really appreciate if anyone could point me how to do that or maybe confirm that its not possible to make it work.

Thanks a lot in advance

---

### Post by linuxwizard on 2008-08-17
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings.
 
 To test your webcam you can do this:
 There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.
 
 If Ekiga didn't work post results of the command > lsusb

---

### Post by java.jfan on 2008-08-18
Hi, First of all, thanks a lot for your answer.
I've tried to test the webcam as you said with Ekiga but it didn't work for me.

My 'lsusb' output is as follows:

Bus 002 Device 012: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 002 Device 011: ID 0424:2602 Standard Microsystems Corp. 
Bus 002 Device 010: ID 0424:2512 Standard Microsystems Corp. 
Bus 002 Device 002: ID 0c45:6260 Microdia 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 0000:0000  

As far as I understand, 
the only thing that can be relevant to me is Bus002 Device 002

The first three lines refer to my DELL WFP2408 monitor which has a card reader and 2 additional usb ports
The Bus 001 Device 002 refers to my coordless mouse/keyboard set

Any help is appreciated

---

### Post by linuxwizard on 2008-08-18
Your webcam > Bus 002 Device 002: ID 0c45:6260 Microdia > for Microdia webcams this is the driver you need > [http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)
Only thing is that I know their are drivers for Feisty & Gusty not sure if one for Hardy if that is what you are using. Look around on the site.

---

### Post by intel on 2008-08-20
0c45:6260 works with the Microdia driver please go here
https://groups.google.com/group/microdia/

---

