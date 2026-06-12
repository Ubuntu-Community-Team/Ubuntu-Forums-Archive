---
title: "Gyration remote"
date: 2012-07-12
forum: Mythbuntu
---

### Post by dotnick on 2012-07-12
I have a question that may seem a bit bazaar.  I have a Gyration Remote GYR3101US.  This remote is written about extensivily for use with lirc and a host of other methods.  Though I've never gotten it to work with lirc, i have been able to use .Xmodmap to do everything I've wanted.  This was all working fine while I was running 11.04.  This past weekend I decided to do a clean install to 12.04.  I have everything back to the way I want it, except the volume keys don't work.  But here's the rub.... they work in XBMC on the same box.  xev doesn't seem to give me any useful information on how to map the keys.  The output strings appear identical between VOLUP and VOLDOWN.

I've read about every post google has put in front of me, so any insight as to where to go next would be appreciated.  I'm baffled that XMBC finds it but MythTv doesn't.  I've tried setting the keymap using the MythTv menus, but MythTv doesn't recognize the keypresses.

---

### Post by dotnick on 2012-07-17
I'm not going to call this solved, because it's really more of a work around.

I decided to install openbox since I wasn't getting anywhere with XFCE.  To my surprise... most of my keys worked as expected with openbox including the volume controls.

There must be a setting in XFCE that is causing a problem with the remote control keys mapping properly (it's a usb RF remote), but I have no idea what it is and at this point... I'm finding myself not caring too much.

---

### Post by speed32219 on 2012-07-19
Thanks for the heads up.  I'm going to go ahead and put some batteries in myg gyration and test it out.  I'll let you know the outomce, I have both wm installed, so it will be interesting to see which one works.

---

