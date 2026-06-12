---
title: "Gusty Boots To Blank Screen"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by mburgoon on 2007-10-18
I downloaded Gusty today (LiveCD) and booted from the disc. The system started up fine and I was able to install the OS. After my first startup in the new system, Ubuntu prompted me to install restricted ATI drivers for my display. I selected 'Yes' to install the dirvers.

I rebooted the system and it boots up to a blank black screen. I restarted... booted into failsafe mode and was able to get to a terminal prompt. I then decided to try and start the GUI interface... so I entered 'startx'. Again my screen went blank.

Obviously the restricted drivers are causing my screen to appear black. Does anyone know how to disable the restircted ATI drivers through the terminal? I could do it through the GUI on my own.... but i can't see anything!

Thanks in advance!

---

### Post by flashman2006 on 2007-10-18
I did a quick Google search and found this link:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Revert_to_Xorg_driver](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Revert_to_Xorg_driver)

So from what I gather, you want to revert back to the Xorg driver (the original video driver that Ubuntu installed) right? Well just follow the instructions at the link and hopefully that will help you.

---

