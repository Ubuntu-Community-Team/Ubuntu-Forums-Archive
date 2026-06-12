---
title: "Can't get back to 16 x 9"
date: 2009-04-17
forum: Multimedia Software
---

### Post by Don DeGregori on 2009-04-17
Ubuntu 8.10 box connected to Sony 40" HDTV. Has VGA in, and 1st I tried it, worked OK. Should have left Screen Resolution alone. Now, Sony shows "Unsupported Signal" and no Ubuntu after final completion of boot. That's when Screen Resolution changes to the error I made. 

LiveCD of 8.10 has no problem, so a wrong parameter was saved on the HD version. Here is what Sony wants:  1920 x 1080 (16 X 9) for this shows up on LiveCD. I think what was saved was 1920 X 1080 (4 X 3)

I need to change something in Ubuntu on the Terminal, but have no idea where to start.

Can someone help?

donde

---

### Post by James_Lochhead on 2009-04-17
If you have an NVidia graphics card you can configure the monitors using nvidia-settings, a program automatically installed when you install the NVidia drivers.

Otherwise you will have to manually edit the xorg.conf file I believe.

---

### Post by Don DeGregori on 2009-04-17
No NVidia, using Intel 945GC Express with Intel Graphics Media Accelerator 950

Should I look at xorg.conf?

donde

---

### Post by James_Lochhead on 2009-04-18
Yea, you could take a look. I wouldn't change anything without good advice though.

---

