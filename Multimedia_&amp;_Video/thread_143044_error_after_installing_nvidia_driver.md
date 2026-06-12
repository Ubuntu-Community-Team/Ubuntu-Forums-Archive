---
title: "error after installing nvidia driver"
date: 2006-03-11
forum: Multimedia &amp; Video
---

### Post by edan on 2006-03-11
i have gforve 4 mx 440 i have installed it and it all worked fine
after i restart the computer an xserver error pops up....

the error syas 

nvidia kernel module is version 1.0.8178 
and x module is 1.0.7667 (and that i shouled upgrade or somthing like that i dont really remember )

failed to intialize nvidia kernel module 
please unsure that the nvisia gpu is seported in this system and that the nvidia device files have been created properly

thats aboute all.... 

what to do?

---

### Post by Princey on 2006-03-11
Try this, type in at the terminal :

sudo cp /etc/x11/xorg.conf_backup_200603061025 /etc/x11/xorg.conf

P.S substitute the 200603061025 with the date and time of when you installed the drivers. I think while you were installing it gave you that message in case of a crash. If that doesn't work, try typing at the terminal 

sudo apt-get install -f 

to force updating and/or removal of any dependencies that might be missing or conflicting. Best of luck.

---

