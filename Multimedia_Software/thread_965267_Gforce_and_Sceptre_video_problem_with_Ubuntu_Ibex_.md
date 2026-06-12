---
title: "Gforce and Sceptre video problem with Ubuntu Ibex 8.10"
date: 2008-10-31
forum: Multimedia Software
---

### Post by lotharjade on 2008-10-31
Ok, I just upgraded to Ubuntu 8.10.  I have an Nvidia Gforce 8200 with the proprietary driver running, and going to a SceptreX22WG-Gamer flat panel via HDMI.  The Nvidia X Server seems to recognize all that, but when I am in the desktop, the video area is not matching the monitor area.  The video is going about an inch past the left of the screen, about a 1/8 inch below the screen, 1/2 and inch above, but yet is within the screen on the right by two inches.  So basically on three sides part of my screen is missing, and on the right I have a 2 inch black bar.  I have not been able to get this to fix.  How can I fix that, and possibly could we get them to fix it with the system for everybody else?

Previously I used EnvyNG and I could rotate through the inputs on the monitor (vga, DVI, HDMI), and it would reset and work properly.  That doesn't work now.  It would be nice if I could get this to work form bootup.

A second smaller issues is that while the NVidia X server recognizing my display, and shows that its native resolution is 1680*1024 (and a different possible resolution) it does not offer that as an option.  How do I fix that?  :confused:

---

### Post by lotharjade on 2008-10-31
Bump, beg.

Do you suppose it is my Monitor or my Driver that is most at fault here?

---

### Post by lotharjade on 2008-11-05
Does anyone have any help or suggestions for me?  I have not found a solution to this problem.  My monitor view is all wonky.  :frown:

---

### Post by lotharjade on 2008-11-19
Come on!  Isn't anyone going to help me here?  Not even a suggestion or anything?  ](*,):-(:frown:

---

### Post by cariboo on 2008-11-19
Have you tried the simple things like using the monitors controls to adjust the screen vertical/horizontal centering and v/h size?

You can use System-->Administration-->NVIDIA X Server Settings to change your screen resolution.

Jim

---

### Post by lotharjade on 2008-11-19
My monitor does not have v/h resize or centering controls.  I have been living with this situation for a couple of weeks.  I am starting to worry that part of my screen might be getting burn in now.  Changing the resolution does not do anything of use.  

Is there a fix to this, or is it a kernel bug?  It is like the Nvidia X Server isn't talking with the screen resolution bit, and there is a bug somehow besides that.

---

### Post by lotharjade on 2008-11-19
I also posted this bug awhile back on launchpad.  It is [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/292320]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/292320").  Would someone look at that and see if I have posted that thing correctly.  I haven't heard a thing, an it has been there two weeks as well.  I worry that I may have not posted it correctly. :-k

---

