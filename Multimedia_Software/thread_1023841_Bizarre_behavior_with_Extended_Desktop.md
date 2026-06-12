---
title: "Bizarre behavior with Extended Desktop"
date: 2008-12-28
forum: Multimedia Software
---

### Post by db163404 on 2008-12-28
Environment
----------------
HP Pavilion dv6000 notebook running 64-bit Hardy.

Background
----------------
I've just purchased a 22" Acer P221W monitor and I'm trying to get an extended desktop environment work properly. I just did a completely fresh install and upon first boot the generic drivers only allow my onboard monitor to be 800x600, so I enable the proprietary nvidia drivers and the onboard monitor is great.

I then plug in the Acer monitor and do a gksu displayconfig-gtk

I select screen 2... extend default screen... to the right.

I choose Acer P221 hit okay... and I'm told I need to reboot, so I do.

On reboot my Acer P221 extended desktop looks beautiful. However, for some reason my on board monitor is now at 640x480 resolution.

I do a gksu displayconfig-gtk and the only option is 640x480... what gives? How can I get extended desktop to work as expected?

---

### Post by db163404 on 2008-12-28
It's a bit of a hack but I've been able to get it to work by manually editing the /etc/X11/xorg.conf file.

Find the section for "Screen" and then locate (or add) the subsection to read as follows:

SubSection "Display"
     Virtual 1024    768
EndSubSection

Save your changes and then restart X (ctrl + alt + backspace).

The resolution should work as expected. The problem with this method is that anytime a change is made to the xorg.conf file (say using a GUI tool) you'll have to go back and manually do this which is definitely annoying.

---

