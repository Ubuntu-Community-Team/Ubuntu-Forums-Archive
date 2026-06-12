---
title: "Geforce 8800GTS maxc resolution of 1024x768"
date: 2007-09-11
forum: Multimedia &amp; Video
---

### Post by gerasmus on 2007-09-11
On my XFX Geforce 8800GTS I'm getting max resolution of 1024x768 and max refresh rate 56Hz (mHz, whetever). My monitor is a Viewsonic TFT capable of 1240x1024, which works fine in WinXP.
During installation (when running the live DVD part) I was able to view 1240x1024. 

I installed nVidia drivers using [Envy]("http://albertomilone.com/nvidia_scripts1.html")  and I'm able to get 3Ddesktop and nice desktop bells and whistles displayed. No other issues, only screen res.
Using a Digital ==> dital video cable.

Any suggestions ?

---

### Post by marquarc on 2007-09-13
have you tried nvidia-settings? Bring up a terminal and type "nvidia-settings", that should bring up a new window wherein you can change the resolution to a higher setting. 

Beware, though... I also have an 8800GTS. I have the same problem you do, and when I use nvidia-settings it works just fine, and looks great. But then when I reboot... it often refuses to start Xorg, stating that there are no available screens. I then have to restore my xorg.conf file to get back in. So I recommend backing up your xorg.conf file first.

---

### Post by dabl on 2007-09-13
If you run it once as ```
sudo nvidia-settings
``` then (a) detect display, (b) set resolution, (c) set refresh (or leave it set to "auto"), and (d) click "Save to X Configuration File", it will make your settings the default when the xserver starts.

Check it by restarting the xserver with Ctrl-Alt-Backspace, log in, and see what you get.  :guitar:

---

### Post by marquarc on 2007-09-13
thanks a lot, dabl. That sure fixed the problems I was having. Much appreciated!

---

### Post by monos98 on 2007-09-13
Thanks!!!  That got me all fixed up!

---

### Post by gerasmus on 2007-09-15
Thanks ! I will give that a try :)

---

### Post by vcarbon on 2007-09-26
I just edited the xorg.conf by hand and added the resolution I wanted. seems to work fine.

---

