---
title: "gnome-volume-control/-applet: non-linear volume scaling"
date: 2010-04-18
forum: Multimedia Software
---

### Post by duchai on 2010-04-18
Hello,
I'm currently running Lucid Lynx and I have a problem with the volume control. My soundcard CMI9761 has no Master channel so that I've adjusted the volume with setting PCM as the default channel on Jaunty or on Kubuntu. Since 9.10 I can't see the option to change the default channel of the volume control.
At a volume of 10%, Master is at 0% and PCM at 47 %. At 20% volume Master is still at 0% and PCM already reached 100%. After 30% Master starts to increase. I read somewhere that this is a feature? But my soundcard has no Master channel so everything above 30% is useless for me as it doesn't increase the volume.
Is there a way to set PCM as the Master channel? Or change the levels that +10% Volume := +10% PCM and not +10% Volume = +50% PCM?

Sorry for my bad english and thanks in advance.

Kind Regards,
duchai

---

### Post by lidex on 2010-04-18
Try the pulseaudio volume control.
Alt+F2
```
/usr/bin/pavucontrol
```

---

### Post by duchai on 2010-04-19
Pavucontrol doesn't solve the problem for me or maybe I haven't found the right option in it.

---

### Post by duchai on 2010-04-20
changing the  /etc/pulse/default.pa file solved it for me. Thanks for your help.

How can I mark the thread as "solved" ?

---

### Post by ericf49 on 2010-05-11
Bonjour,

Il suffit de taper dans un terminal.

Code:
gnome-volume-control-applet &

et par enchantement il revient , je ne sais pas, pourquoi ni comment,

---

### Post by dbloom on 2010-05-11
Hi,

I'm having the same exact problem.  Can you explain what you changed in the default.pa file?  

Thanks!

---

### Post by ChrischanM on 2010-06-14
Hi at all,

duchai sent me his solution (it works for me - but don't change pulse audio settings!):

In /etc/pulse/default.pa I have changed the line

```
#load-module module-alsa-sink
```to

```
load-module module-alsa-sink control=PCM
```and 

```
load-module module-udev-detect
```to

```
load-module module-udev-detect ignore_dB=1
```After a restart  of pulseaudio or your machine, it should only control your PCM Channel.  You could type alsamixer in terminal to look up which volume bar is  changing.

Regards,
duchai

---

