---
title: "ATi Multi-Monitor settings don't stick"
date: 2008-12-12
forum: Multimedia Software
---

### Post by Mephi on 2008-12-12
Hi,

I'm trying to setup my screens to work at their native resolution.
I've got one that runs at 1680x1050 and another at 1280x1024.

I managed to get them to run correctly, but the settings don't stick.

It boots with both screens set at 1280x1024.

To get them to work I do the following steps through the ATi Catalyst Control Center:
1. disable the second screen (1280x1024)
2. Reboot
3. Set the first screen to it's correct resolution (1680x1050) which wasn't available before the reboot.
4. add the second screen in.
Then it works, until I reboot. 

Any ideas why?

Mephi

---

### Post by markbuntu on 2008-12-12
Some people with this particular problem have fixed this by setting up their screens the way they want and then going to System/Preferences/Screen Resolution, letting it open and then just clicking close.

---

### Post by Mephi on 2008-12-13
Thanks for responding. I gave that a go, and it didn't work.

I did however discover that restartung gnome with ctrl-alt-backspace had the same effect as restarting, so that's cut my boot time to a usable desktop down to about 8 minutes...

---

### Post by MiD-AwE on 2009-05-17
You're doing better than some. I have not been able to use my full desktop on dual monitor setup, and no 3D support on a multimonitor setup. I have both monitors set correctly but half of my second monitor wont let me drag windows or basically use any of the desktop at all. I read that the X11 has changed and there are many issues with multimonitors, some of which I haven't been able to get far enough along to run into.

---

### Post by Mephi on 2009-05-18
Well, I have since upgraded to 9.04 and it all seems to be working now.
Using the closed drivers and the Ubuntu screen settings tool and it all seems fine :-)

Mephi

---

