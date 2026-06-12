---
title: "How to Enable Network"
date: 2011-12-12
forum: Networking &amp; Wireless
---

### Post by pumpkinpatch on 2011-12-12
I can no longer access Wireless
My Network Manager Icon left my panel one day. I would love to have one but it doesn't exist in my Panel applications list.  I don't seem to be able to access this through Systems or my Preferences. Is there another way?  Can I get my icon back? I did check through terminal to find out if it was enabled and indeed it said no.  what do i do now?

---

### Post by praseodym on 2011-12-12
Try
```
nm-applet
```
in the terminal

---

### Post by pumpkinpatch on 2011-12-12
I tried it 

An instance of nm-applet is already running.

** (nm-applet:5233): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

---

### Post by praseodym on 2011-12-12
With this error message: Create a starter on the desktop with "nm-applet", click it repeatedly to see where in the panel something happens. If you get this: Click on it, un-checkbox "activate network", and checkbox it again. Now it should work

---

### Post by pumpkinpatch on 2011-12-12
With this error message: Create a starter on the desktop with "nm-applet",

I think I'm missing something because I don't understand how to create an nm-applet from the desktop.

---

### Post by praseodym on 2011-12-12
Create a starter in your menu and pull it onto the desktop. Which Ubuntu version is that?

---

