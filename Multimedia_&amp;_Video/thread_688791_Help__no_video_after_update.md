---
title: "Help:  no video after update"
date: 2008-02-05
forum: Multimedia &amp; Video
---

### Post by scamper_22 on 2008-02-05
Hi, 
I installed some updates (icon popped up saying updates are available).
It then said, it needed to reboot.
So I rebooted, and since then I've been unable to get the GUI back.  It's stuck at the command line.

Right now, I'm back in VESA mode after running sudo dpkg-reconfigure xserver-xorg
Now, it flickers the command prompt login and then goes into vesa (800x6000 mode.

I've got an Nvida geforce 4 go 32MB.  This used to work fine.  I've reenable the driver in the restricted drivers manager, but still the same thing.

Any help on this?  is there anything I can check or logfiles I should check?


Thanks,

Y

---

### Post by carlinuxlearner on 2008-02-05
You could try installing it with "Envy" [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) 
it almost always works for me, though some times I have to do it more than once.
This will happen every time you update the kernel (which is what you did) you have to reinstall the Nvidia kernel module (install the driver again).

C@RL

---

### Post by scamper_22 on 2008-02-05
nice :)

yeah, i actually had orignially installed the driver via envy. 
I reinstalled it again via envy and now its working.

Good to know why it needs the envy (update kernel).
Thanks for z info.

Y

---

