---
title: "Firefox crashes when flash video played"
date: 2009-10-25
forum: Multimedia Software
---

### Post by cusri2004 on 2009-10-25
Hi forum,

Recently my firefox 3.0 browser keeps crashing sometimes when I play flash media. I have googled this issue but there is no clear answer as such why it happens and whats the remedy. So here I am. 

I ran firefox from terminal and here is the output

sometimes it is 

** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault

and some other times
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(firefox:10823): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

---

### Post by lovinglinux on 2009-10-25
I recommend installing Firefox 3.5. You can do it manually or you could wait for Ubuntu Karmic release, which will be available in less than a week. It has Firefox 3.5 by default.

Flash is very problematic in Linux, but in Firefox 3.5 works better. Nevertheless, you could try some things from the Flash Optimization section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

You will also find most popular methods of installing newer Firefox versions on that tutorial.

---

