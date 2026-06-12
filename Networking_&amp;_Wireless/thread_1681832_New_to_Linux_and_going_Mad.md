---
title: "New to Linux and going Mad"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by electricpoet41 on 2011-02-04
Basically this is my only and main issue and i can't seem to figure it out no matter how much time i spend on it.  When running the Ubuntu Netbook LIVE to test it out, a thing popped up about my wireless, i then connected it hardwired so it can download the correct firmware etc.  Which it did, everything worked GREAT!  So I then did an install of it onto my local hard drive.  Of course, Of course, nothing ever popped up, it won't recognize my wireless... I tried installing several things and im just lost.... PLEASE HELP!

---

### Post by electricpoet41 on 2011-02-04
oh and by the way of course since im new to this, i did something and now hardwired doesn't work either... i think i removed something... who knows please help... btw its a Dell Insspiron B130

---

### Post by sffvba[e0rt on 2011-02-04
Seeing as this is a new install and all you have to loose is time you could always do a re-install... and this time not "remove" anything...


404

---

### Post by arrimapirate on 2011-02-04
Reinstall then after it boots plug in the ethernet cable so you can get online. Then go to System->Administration->Additional Drivers and it should display your wireless card/any other drivers you might need. 

Your problem was that you installed the driver to the live system. It was deleted as soon as you rebooted.

---

### Post by frogotronic on 2011-02-05
> **not found said:**
> Seeing as this is a new install and all you have to loose is time you could always do a re-install... and this time not "remove" anything...


404

Yep, do the install over, and when it gives you the option of installing "side by side" , DON'T choose that option -> choose "Erase/Use entire disc".

Plug in an ethernet (T3/T5) cable and the machine will then allow you to install wireless.  If the Wireless drivers aren't automagically downloaded.

Go to: System>Administration>Hardware Drivers and (it may ask you for a password) it will scan for the wireless and possibly graphics drivers.  Highlight the ones you need (usually STA for wireless).  I believe this machine has Intel Graphics, which should be included in the kernel.

Post back and we'll help you through the rest.

- CH

---

