---
title: "Can't get screen resolution &gt; 800x600"
date: 2008-12-30
forum: Multimedia Software
---

### Post by scharkalvin on 2008-12-30
I installed 8.10 on an AMD64 system with a GeForce 7600GT graphics card.

I can't get more than 800x600 (sounds familiar!)

I activated the Nivida graphics driver and rebooted, but when I go back to the hw drivers applet it still tells me the driver isn't activated.

Maybe I need to install the driver with apt-get or something?

sudo dpkg-reconfigure xserver-xorg  does NOT ask ANY questions about the screen resolution.  I think a different package needed to be reconfigured to do that.

sudo xrandr -q   returns Can't open display

sudo nvidia-settings  returns  ERROR: the display is undefined
(BTW I had to do apt-get update  then apt-get install nivida-settings since this app wasn't installed with the system).

So where do I go from here?

---

### Post by scharkalvin on 2008-12-30
After a reboot the system offered to install updates.
After doing THAT, I was FINALLY able to REALLY install the -177 version of the Nvidia drivers.  Now the nvidia config utility seems to work.

---

