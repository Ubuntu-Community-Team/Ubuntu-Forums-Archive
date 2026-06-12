---
title: "24 Hours In &amp; My Display is Gone"
date: 2008-06-29
forum: Multimedia Software
---

### Post by msutherland91 on 2008-06-29
Less than a day into Linux and I've managed to already screw up my display!

Ok, I've been trying to install the nVidia Linux x86 video driver for my GeForce 8800GTS and then I finally got it installed. I installed it as follows:

> 
sudo -s
sudo /etc/init.d/gdm stop
sh NVIDIA-*.run
((install worked))
exit
exit
(CTRL-ALT-DEL)


Then, when Ubuntu booted back in it was running in "low graphics mode" so it was at a 800x600 resolution as opposed to my previous 1280x1024. So I wasn't sure what I did wrong and eventually went to do the following:

> 
sudo -s
nvidia-xconfig
((nothing happened))
sudo /etc/init.d/gdm restart
((nothing))
sudo /etc/init.d/gdm stop
((nothing))


Still nothing. So I uninstalled the nVidia driver, hoping it would restore my previous settings. Nope. So I turned back on the proprietary driver after doing the following:

> 
sudo /etc/init.d/gdm reload


And then, when I restarted and booted back in, it was not only in low graphics mode still, but only displayed the upper half of the screen where the lower half was and wrapped the display around, overlapping. Above that the screen is black and full of artifacts. I  have no idea how to fix this. I'm currently running off my other partition in Windows XP so as to type this.

Please help.

---

### Post by L337_K3y5 on 2008-06-29
If you're just 24 hrs. in I don't see a reason as to not just reinstall, I mean its not like building Gentoo or nothing, took me a few min. on my second round.  As to your question, thats wierd, I installed my ATI card easily, I don't know how well the Nvidia cards go over...:-k

---

### Post by msutherland91 on 2008-06-29
Meh. I really don't want to have to reinstall. But it's near impossible to do anything within the X server so anything that can fix it I would have to do in the console.

---

### Post by xc3RnbFO8P on 2008-06-30
How did you install?
Did you choose restricted Nvidia driver, 
downloaded the updates and then restarted?
Or choose the restricted Nvidia driver and restart,
then download the updates and restart?

---

### Post by msutherland91 on 2008-06-30
I have no idea, but I don't remember downloading any updates.

---

### Post by xc3RnbFO8P on 2008-06-30
Dont you have a update Icon in upper right corner on the panel?

---

### Post by untermensch on 2008-06-30
Try booting up your Ubuntu partition again. When it gets there and is all messed up hit ctrl + alt + f1. You'll see an all black screen with white letters (just covering if you don' know, don't take this as insulting please) type in your username and password. once you do that type sudo shutdown now. it should come to a point where there are 4 options. one of them is fix x or xfix or something along those lines, scroll down to that one and hit enter. it should attempt to fix your display.

---

### Post by xc3RnbFO8P on 2008-06-30
Read this:
[http://ge.ubuntuforums.com/showthread.php?t=798881]("http://ge.ubuntuforums.com/showthread.php?t=798881")

---

