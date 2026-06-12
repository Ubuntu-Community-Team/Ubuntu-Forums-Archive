---
title: "Nvidia 7500LE"
date: 2008-01-28
forum: Multimedia &amp; Video
---

### Post by trebor147 on 2008-01-28
Hey guys,
I have just reinstalled my Ubuntu 7.10 from a remastersys backup disc.  Everything is as it was apart from my graphics drivers.

So I looked into Restricted Drivers Manager and the box was unchecked.  So I checked it, it downloaded the files and all was well I thought.  This process has worked various times in the past,

On reboot I get problems.  I get a message about my display settings, the system then resets to very low standards.  I get a box that says always run in low settings, configure or reboot (or something similar).  I tried manually configuring but that didnt help.

WIth the driver installed, supposedly that is, my resolution is very low and the quality of the display is awful.  WIth the driver unchecked in Restricted Drivers Manager my display is much better, higher resolution etc.

Whats going on?  This always worked in the past.  Any ideas?


Thanks, Robert,

---

### Post by overdrank on 2008-01-29
> **trebor147 said:**
> Hey guys,
I have just reinstalled my Ubuntu 7.10 from a remastersys backup disc.  Everything is as it was apart from my graphics drivers.

So I looked into Restricted Drivers Manager and the box was unchecked.  So I checked it, it downloaded the files and all was well I thought.  This process has worked various times in the past,

On reboot I get problems.  I get a message about my display settings, the system then resets to very low standards.  I get a box that says always run in low settings, configure or reboot (or something similar).  I tried manually configuring but that didnt help.

WIth the driver installed, supposedly that is, my resolution is very low and the quality of the display is awful.  WIth the driver unchecked in Restricted Drivers Manager my display is much better, higher resolution etc.

Whats going on?  This always worked in the past.  Any ideas?


Thanks, Robert,

HI and you may try to configure you xorg, when you reach the login screen ( or you receive the error of low graphics mode)  use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and  when complete use the command to reboot ```
sudo reboot
``` or ***startx *** also you may want to look at Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Hope this helps and good luck!

---

