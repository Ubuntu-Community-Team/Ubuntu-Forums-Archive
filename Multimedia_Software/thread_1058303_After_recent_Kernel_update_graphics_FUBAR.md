---
title: "After recent Kernel update graphics FUBAR"
date: 2009-02-02
forum: Multimedia Software
---

### Post by //yardo on 2009-02-02
Ok so after the recent kernel updates (last week) my resolution settings have gone away and have yet to return.

I'm running a KDE kiosk live cd. Previously the install would detect the native resolution of the monitor and run accordingly with that resolution. Now that doesn't work and it forces a 1280x768 resolution and the desktop is skewed.

WHAT HAPPENED?! This has become kinda frustrating because I have a new release of my kiosk live CD that I need to publish out to customers with new features and this is holding me up.

I tried reconfiguring xserver and even deleting the xorg.conf file.

Nothing seems to work. What can I do?

---

### Post by Crafty Kisses on 2009-02-02
What kind of video card do you have?

---

### Post by //yardo on 2009-02-03
It's an ATI.

---

### Post by markbuntu on 2009-02-03
An ATI what?
What driver were you using for this card and where did you get it.

---

### Post by //yardo on 2009-02-04
Apparently the VGA cable was half unplugged. Graphics are fine now. :rolleyes:

I spent days trying to figure this thing out and almost started a fresh rebuild purely out of frustration.

---

