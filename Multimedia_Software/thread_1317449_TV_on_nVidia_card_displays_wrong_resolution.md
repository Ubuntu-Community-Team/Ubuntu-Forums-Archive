---
title: "TV on nVidia card displays wrong resolution"
date: 2009-11-06
forum: Multimedia Software
---

### Post by tstack77 on 2009-11-06
I am trying to setup xbmc to run on my tv through the second output on my video card. I have no problems registering my HDtv resolution in windows (1920x1080), but in nvidia-settings the highest output resolution is 1024x768.

To make matters even worse, when I try to save the second monitor/tv in nvidia-settings I get an error "Failed to parse existing X config file '/etc/X11/xorg.conf" (seg fault on exit), so I cannot even go into xorg to manually change the resolution.

Any ideas where to start to tackle this issue? I am on a fresh karmic x64 install and have a gtx260.

---

### Post by HappyFeet on 2009-11-06
First you need to delete your xorg.conf file. Then open nvidia-settings and do what you were going to do in the first place. When you go to save the settings, it will see that you do not have a xorg.conf file. A box will pop up asking where to put the info. At the top of the box there is a button that says (I think) "show output". Click that and copy the contents. Now you can go back and create another xorg.conf file and paste what you copied before. Save then restart.

---

### Post by tstack77 on 2009-11-06
Sweet, that worked to allow me to save. I still have the issue with the TV out though. I tried to manually change the resolution but it didn't take. How can I force the correct resolution and have it recognized?

---

### Post by tstack77 on 2009-11-07
Any one figured this TV out resolution situation?

---

### Post by tstack77 on 2009-11-08
Any guesses or explanations?

---

