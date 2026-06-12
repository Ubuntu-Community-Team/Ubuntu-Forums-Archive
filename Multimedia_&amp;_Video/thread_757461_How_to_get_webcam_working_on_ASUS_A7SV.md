---
title: "How to get webcam working on ASUS A7SV"
date: 2008-04-16
forum: Multimedia &amp; Video
---

### Post by penguinhack62 on 2008-04-16
Hello, I am trying to get my webcam working on my ASUS A7SV. Can anyone steer me in the right direction? Any help will be greatly appreciated.

---

### Post by linuxwizard on 2008-04-17
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If cam does not work post the results of the command > lsusb

---

### Post by penguinhack62 on 2008-04-17
this is my output of lsusb:

Bus 007 Device 001: ID 0000:0000
Bus 006 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 002: ID 0b05:1712 ASUSTek Computer, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 174f:a311
Bus 001 Device 001: ID 0000:0000


It doesn't seem like webcam is detected. Program doesn't detect webcam either.

---

### Post by linuxwizard on 2008-04-17
No webcam listed. Only thing I can think is check your computer Bios see if cam is disabled.

---

### Post by penguinhack62 on 2008-04-17
No, everything in bios is on. Do I need to install some drivers maybe? If so, which ones?

---

### Post by linuxwizard on 2008-04-17
No you don't need to install any drivers yet. Your system is not detecting your webcam. Which version of Ubuntu are you using ?

---

### Post by penguinhack62 on 2008-04-17
I am using 7.10

---

### Post by penguinhack62 on 2008-04-17
I just removed Vista Premium from this laptop. Was having many issues with windows programs, word etc... Vista kept crashing. I decided to put Ubuntu on because I never tried it.  Have always been a Suse advocate.  I know the webcam was working with Vista because I had just used it prior to switching over.

---

### Post by linuxwizard on 2008-04-18
This is your webcam > Bus 001 Device 002: ID 174f:a311 > according to this > [http://syntekdriver.sourceforge.net/index.php?mode=faq](http://syntekdriver.sourceforge.net/index.php?mode=faq) > when I did a search last nite it came up USB Adapter or Bluetooth device. Not sure what I did their. But this looks like the driver you need > [http://sourceforge.net/project/showfiles.php?group_id=178178](http://sourceforge.net/project/showfiles.php?group_id=178178)

---

### Post by mfreeze1 on 2008-04-19
Hey your answers so great.. can you help another out?

lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 003 Device 002: ID 0c45:627b Microdia 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


Using 7.10 and yes the camera worked on the computer before diving into Linux..

tried Ekiga and tried the video settings and just had a Ekiga bouncing logo

any help?  been searching forums till numb.. sorry for butting in on the post..

---

### Post by linuxwizard on 2008-04-20
mfreeze1
For Microdia webcams you need the driver from here > [http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)

---

### Post by elektriks on 2008-04-20
maybe install webcam driver

---

### Post by intel on 2008-05-02
> **mfreeze1 said:**
> Hey your answers so great.. can you help another out?

lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 003 Device 002: ID 0c45:627b Microdia 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


Using 7.10 and yes the camera worked on the computer before diving into Linux..

tried Ekiga and tried the video settings and just had a Ekiga bouncing logo

any help?  been searching forums till numb.. sorry for butting in on the post..
Theres already a working driver for this webcam here
[https://groups.google.com/group/microdia](https://groups.google.com/group/microdia)

---

