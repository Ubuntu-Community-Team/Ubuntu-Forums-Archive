---
title: "nvidia driver, 1440x900 monitor, xorg.conf"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by explainer on 2007-05-08
I just installed 7.04 on a new AMD 64 dual-core system.  It has an NVIDIA 6100 on the motherboard (GIGABYTE).  I installed the system at the dealer's shop with a default 1024x768 configuration. When I got back to my office, I enabled the nvidia restricted drivers and then attempted to set my screen resolution to fit my ViewSonic VA1912wb , which is 1440x900.  The selections available don't support that resolution.  I am guessing now that I have to edit the xorg.conf file, but I don't have a clue how to define the "Monitor" or "Screen" sections, and can't find any good documentation on X-Windows (lots of documentation, none of it good).  Can someone please give me an example?

---

### Post by anachreon_ on 2007-05-08
Hi explainer, do you use Gnome (Ubuntu) or KDE (Kubuntu)?  I don't know my way around Gnome, but in KDE you can access the nvidia control panel by hitting alt+f2 to run a command, and then typing "kdesu nvidia-settings" to bring up the control panel as super user.  I'm sure there is an analogous way to do this in Gnome.  That might be a good place to start to see what resolutions the driver thinks it can support.  Under "X Server Display Configuration" you change your screen resolution and save it out to the xorg.conf file.  Then when you restart the X Server, you should be set.

I've found nvidia-settings to be the best way to change this sort of thing before using other methods, so try that first and let us know if you have any success.

---

### Post by zeusalmighty on 2007-05-08
DOH!! Man I feel like an idiot right now!! LOL! I was wasting my time trying to find an answer for this in here, when there's a panel that does that for you?! Ugh.... thanks mate!

---

### Post by explainer on 2007-05-08
Thanks for the nvidia-settings command.  That should really help in the future.  Funny thing, but right after I posted my query, I did a complete shutdown and reboot for other reasons, and the next time I checked Preferences->Screen Resolution, there was my 1440x900 option.  I selected it and I am now a happy camper.

---

### Post by anachreon_ on 2007-05-09
Glad to hear it worked out.  Good luck with everything.  :)

---

