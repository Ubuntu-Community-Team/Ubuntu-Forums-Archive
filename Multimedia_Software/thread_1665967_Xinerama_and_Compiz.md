---
title: "Xinerama and Compiz"
date: 2011-01-13
forum: Multimedia Software
---

### Post by dr.frankinfurter on 2011-01-13
I didn't find a thread that addressed all my issues and the ones I did find were dead threads that were horribly outdated. If I missed a post that included a description and solution of my problems then I apologize.

I set up a dual-monitor display using nvidia-settings tool. I have two separate x screens which are joined together using xinerama. For the most part, I have what I want running: Two x screens that are independent of one another but open applications can be moved between monitors.

The problem is that Compiz doesn't want to run and that sucks. I can get Urban Terror to run on one monitor but the mouse doesn't want to move around. How do I get Compiz to work? What is a good solution for video games?

I was able to find some resources online but none of them were really updated (2007-2008 mostly). When I attempted to run compiz from the command line I got this output:

> tyler@tyler-desktop:~$ compiz
compiz (core) - Fatal: No composite extension

Launching fallback window manager
Xlib:  extension "RANDR" missing on display ":0.0".



I have attached my xorg.conf file.

Any help would be greatly appreciated.

---

### Post by xjcannonx on 2011-01-21
I had thought I had this working in 10.04 but after upgrade to 10.10 this no longer works.

It is really frustrating, all the research I did says this combination can't work. For all the flaws of windows, the display manager works great. The Ubuntu folks really needs to address this issue.

---

