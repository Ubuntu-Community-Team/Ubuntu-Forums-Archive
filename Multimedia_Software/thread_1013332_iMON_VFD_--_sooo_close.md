---
title: "iMON VFD -- sooo close"
date: 2008-12-16
forum: Multimedia Software
---

### Post by Coruba67 on 2008-12-16
Hi guys,

Am using an iMON VFD device and have gone through and set it up thanks to a few forum posts around - when I run 

sudo LCDd -f -r 4

in the terminal it comes up and changes the display on the VFD - so this is telling me the drivers are working.  

Something else thats interesting here is that it says its Listening for Queries on 127.0.0.1:13666 in the terminal

When exiting out of this it displays

"Thanks for using
LCDProc and Linux"

I just can't get Myth or anything else to display anything on it.  I have configured Myth to use an LCD Device in the Appearance settings but nothing seems to happen, it just keeps saying Thanks for using LCDProc and Linux.  I know it must be something really small but how do I get Myth to display the various options on the panel?



Thanks for any help in advance!

---

### Post by Coruba67 on 2008-12-17
Ok update, I have this now displaying the information on mythlcdserver - but only if I run that command 

sudo LCDd -f -r 4 

and then in a seperate terminal run lcdproc then open myth... 

How do I get those two things to run automatically on bootup!?

---

