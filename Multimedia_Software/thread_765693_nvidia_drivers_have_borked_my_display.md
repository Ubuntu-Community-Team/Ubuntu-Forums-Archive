---
title: "nvidia drivers have borked my display"
date: 2008-04-24
forum: Multimedia Software
---

### Post by dingfelder on 2008-04-24
arggggg !!!

I was having issues where I had some graphics slowness (logging in sometimes took 10 min for instance) and firefox would lock my x session, so I went to the admin propiatory drivers section and told my system to use the nvidia drivers.

I rebooted and now my desktop is shown (I can see the background image) but there are no menus or icons.  right clicking the desktop allows me to change the background image.

I assume I need to change back to the old driver to use x now

I went into console mode and change my xorg.conf file to use the nv driver instead of nvidia but upon logging in, the same things occurs.  so I assume either it it not the driver causing the issue, or the changed conf file is ignored and the nvidia driver is still in use.

How can I manage propiatory drivers non-graphically so I can revert back?  or is there something else I can try? :confused:

---

### Post by overdrank on 2008-04-24
> **dingfelder said:**
> arggggg !!!

I was having issues where I had some graphics slowness (logging in sometimes took 10 min for instance) and firefox would lock my x session, so I went to the admin propiatory drivers section and told my system to use the nvidia drivers.

I rebooted and now my desktop is shown (I can see the background image) but there are no menus or icons.  right clicking the desktop allows me to change the background image.

I assume I need to change back to the old driver to use x now

I went into console mode and change my xorg.conf file to use the nv driver instead of nvidia but upon logging in, the same things occurs.  so I assume either it it not the driver causing the issue, or the changed conf file is ignored and the nvidia driver is still in use.

How can I manage propiatory drivers non-graphically so I can revert back?  or is there something else I can try? :confused:

Hi and welcome, when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by dingfelder on 2008-04-24
ok, got home and tried it, and it didn't help.  It produced a warning that it was overwriting the conf file but didn'n ask any questions.  after rebooting, no change.  

anything else I can try?

---

### Post by overdrank on 2008-04-25
> **dingfelder said:**
> ok, got home and tried it, and it didn't help.  It produced a warning that it was overwriting the conf file but didn'n ask any questions.  after rebooting, no change.  

anything else I can try?

Ok I had a similar issue the other day. What is the model of the graphics card and what version of ubuntu are you using?

---

### Post by dingfelder on 2008-04-27
compaq presario r3000 laptop, has an integrated geforce card, if memory serves me it is a GeForce 4 440 Go 64M

I am not 100% sure the cause, and if it indeed the graphics driver, as I thibnk I was able to get it using the nv driver and it is still acting strange.

What I observe is that when I start it up, X starts in about 10 seconds (I see a tan background), then about a minute later white toolbars appear, with no menu options.  A minute later perhaps, the menu items appear, but are not appearing to be listening to clicks.  Then any open apps I had running start up such as a terminal window.

If I click a menu and come back 10 or 20 minutes later, the ssytem may have finally responded to the click.

It seems that perhaps something is hogging the UI and making everything unresponsive or something.

---

