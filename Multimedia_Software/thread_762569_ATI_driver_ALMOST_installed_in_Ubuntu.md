---
title: "ATI driver ALMOST installed in Ubuntu"
date: 2008-04-22
forum: Multimedia Software
---

### Post by ladysun1 on 2008-04-22
Hello there!  

I am new to Ubuntu and wanted to configure drivers for my graphics card an ATI 1650 AGP but only got half way.  I succeeded with installing the drivers I downloaded from the ATI site(under root) but I think I was supposed to configure them on the Linux side.  When I start Ubuntu I get everything but the final desktop.  There is only a white background and my cursor.  I am able to get to the Failsafe mode that is why I think I need some script to pull everything together.
Decided not to go with the "restricted" drivers because I got fatal errors with those.  Can someone help me out?  Thanks:(

---

### Post by aaronp on 2009-04-14
if you made a backup of your xorg.conf then when you boot into failsafe mode just overwrite the current xorg.conf with the backup copy and restart again - this should put it back to where it was before the changes.

I had a fair few issues trying to install drivers for my card and my absolute saviour was an app called envyNG. It detects the card and monitor and installs everything for you within 5 mins.
Not sure if it works for all cards but it worked perfectly for mine.

hth
AAron

---

### Post by markbuntu on 2009-04-14
If you have ati I would not reccomend ENVY, it misinstalls the driver a lot. Did you get any errors when you installed the driver?
If you did not get any errors installing the driver

In failsafe from the command line run

aticonfig --initial -f

---

