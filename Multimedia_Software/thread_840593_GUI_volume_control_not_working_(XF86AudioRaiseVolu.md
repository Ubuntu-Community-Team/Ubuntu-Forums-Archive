---
title: "GUI volume control not working (XF86AudioRaiseVolume etc)"
date: 2008-06-25
forum: Multimedia Software
---

### Post by quadCoreBrainWithNoMemory on 2008-06-25
I just upgraded to 8.04.  
The up/down volume keys on my keyboard will only let me adjust volume between 89% and 100% but I hear no difference.  I try to rebind the keys with various global shortcuts using kmix, amarok, and other applications, but it doesn't work.  I get this volume bar when adjusting volume:
[IMG]http://farm4.static.flickr.com/3088/2610608063_df21f183fe.jpg?v=0[/IMG]

As I said, redefining my media key buttons with various global shortcuts doesn't help.  It shows the keyboard volume keys as 
XF86AudioRaiseVolume, XF86AudioLowerVolume
And I have tried to use these in global shortcuts for kmix, the Sound Mixer applet, and Amarok.  I'm thinking the volume keybindings are done with X at a level before kde's shortcuts system can handle the events, but I'm not sure how to find out or stop it.

Other possibly relevant information:
I run gdm, but use kde as my desktop
I'm using the Microsoft Natural Ergonomic Keyboard 4000
/etc/issue lists "Ubuntu 8.04"

---

### Post by Odrodzona-Sarmacja on 2008-06-26
If you're using ALSA sound driver, then install alsamixergui package. You should be able to fix all issues then with it for all your ALSA apps.

---

### Post by quadCoreBrainWithNoMemory on 2008-07-01
> **Odrodzona-Sarmacja said:**
> If you're using ALSA sound driver, then install alsamixergui package. You should be able to fix all issues then with it for all your ALSA apps.

I am guessing this is a x keybindings issue at the x server level or window manager level.  Since kwin's settings don't seem to show the keybindings for this, I am not sure how to address it.

I did fiddle around the with the application you noted, but didn't find anything that that obviously would work.

---

