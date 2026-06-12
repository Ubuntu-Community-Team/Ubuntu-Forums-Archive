---
title: "This is an embarrassment Ubuntu running low in resolution"
date: 2008-08-10
forum: Multimedia Software
---

### Post by dr_alejandro on 2008-08-10
I am really really disappointed with Ubuntu. I have a dual boot XP and Ubuntu 8.something (I can't check because I cant reach the menu button thanks to the resolution). Ubuntu was working fine, even the advance graphic effects were working without issues. I have not use Ubuntu for about two weeks and today when I did I runs in low resolution (800x600) I believe. I try to start it in recovery mode and same story. Before logging in it give me the option to search for my graphics card an Nvidia 8600gt but that didn't fix it. I have an HP w2207 monitor, 22" and the resolution I use is 1680x1050, well not anymore.

Do I have to go and manually change the xorg file (or whatever file that was)? I dont want to do that. That is something I did when I installed the 7.0 version of Ubuntu. Are we moving backwards? What is going on?

Is there any update that has created this problem in the last few weeks?
It is so annoying using this resolution that is a pain in the rear to navigate the forums.

I am talking out of frustration right now but this is really the kind of silly problems that keep people away from linux. I dont see the advantage of changing to linux full time with this type of problem. Im lucky Im not on a deadline today. I ... I ... oh man I just need a beer.

---

### Post by wolfen69 on 2008-08-10
do
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` 
then restart x or reboot.

i've installed ubuntu on well over 20 different machines without any problems. perhaps it is your computer at fault and not ubuntu. (people don't want to admit this) next time buy a computer with linux instead of something made for windows, and it will be a different story.

---

