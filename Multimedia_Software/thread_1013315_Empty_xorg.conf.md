---
title: "Empty xorg.conf"
date: 2008-12-16
forum: Multimedia Software
---

### Post by cfwells1 on 2008-12-16
I have installed 8.1 on an old IBM laptop. Everything is fine except I cannot get 1024x768 resolution.  My xorg.conf file is empty, so what do I edit to get the desired resolution? There must be a file somewhere that limits the resolution to 800x600.  My monitor shows up as "unknown"  I know it supports 1024x768.  Why is there no xorg.conf file?

---

### Post by SuperSonic4 on 2008-12-16
Have you looked in /etc/X11/xorg.conf for it?

---

### Post by cfwells1 on 2008-12-16
yes, the file is empty

---

### Post by benerivo on 2008-12-16
I think the new version of xorg does not use a xorg.conf file by default, although it can do. I would set one up with```
sudo dpkg-reconfigure -phigh xserver-xorg
```Then edit it so it includes...

Section "Screen"
 DefaultDepth 24
 SubSection "Display"
  Viewport 0 0
  Depth 24
  Modes "1024x768"
 EndSubSection
EndSection

---

### Post by cfwells1 on 2008-12-16
I will try that now.  If 8.1 doesnt usexorg.conf, what does it use to configure the video and monitor?

---

### Post by benerivo on 2008-12-16
Backup first, and wait 10 mins for potentially better answers. I don't know how the new xorg works, other than it just seems to use the hardware default/native settings. I think most users who add restricted drivers will have a xorg.conf generated for them so that it won't use the defaults.

---

### Post by cfwells1 on 2008-12-16
I edited the xorg.conf file but I cannot save.  It says I do not have permission.  I am the root user but I cannot login as root.  How do I save the file?

---

### Post by benerivo on 2008-12-16
Edit the file 'as root' with```
gksudo gedit /etc/X11/xorg.conf
```in a terminal window.

---

### Post by cfwells1 on 2008-12-16
I did the edit.  Got a message that Ubuntu could not parse the file and It started in low graphics mode.  I have a xorg file from puppy linux on the machine that works,  I will try and paste that into xorg and restart again.

---

### Post by cfwells1 on 2008-12-16
Well if its of interest to anyone, I pasted the device,screen, modes and monitor section from puppy linux xorg.conf into the xorg.conf  of ubuntu 8.1 and I finally got 1024x768 displayed on the screen.  I find it strange that puppy linux could configure the video properly and Ubuntu could not.  Thanks for your help.

---

