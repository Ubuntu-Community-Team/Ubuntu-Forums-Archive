---
title: "Need help with Repository ATI driver Configuration on 8.10"
date: 2008-12-11
forum: Multimedia Software
---

### Post by dontgvadamn on 2008-12-11
I have been fighting with this for a couple of days now...I am trying to setup dual head mode with the repository driver in the hardware manager. I fought with the driver for awhile, It was causing the screen to bunch up on scrolling....but oddly enabeling Compiz Fusion solved that. So now As it stand I have the repository driver installed and both monitors display but they are in clone mode...I dont want big desktop, but rather the setup where screen 2 is to the right of screen one.

I tried running this command:
```
sudo aticonfig --initial=dual-head --screen-layout=right
```
It worked to make the desktops appear left and right, but I lost all my menu bars and could not do anything.

Here is what my xorg.config looks like as of now:
```
Section "Monitor"
   Identifier   "Configured Monitor"
EndSection

Section "Screen"
   Identifier   "Default Screen"
   Monitor      "Configured Monitor"
   Device      "Configured Video Device"
   DefaultDepth   24
EndSection

Section "Module"
   Load   "glx"
   Disable   "dri2"
EndSection

Section "Device"
   Identifier   "Configured Video Device"
   Driver   "fglrx"
EndSection
```

If anyone could help it would be much appreciated...I like this setup becuase I can run a virtual machine on the second display and the background isnt weird.

---

### Post by markbuntu on 2008-12-11
You should use the Catalyst Control Center for that.

---

### Post by dontgvadamn on 2008-12-11
Catalyst Control Center Only allows you to switch to Big desktop. It doesnt have options for the side by side dual head setup.

---

### Post by markbuntu on 2008-12-11
You can move the monitors around with the CCC and swap display 2 and display 1.

---

