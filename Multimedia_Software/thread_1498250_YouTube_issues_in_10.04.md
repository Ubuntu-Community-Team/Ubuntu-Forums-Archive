---
title: "YouTube issues in 10.04"
date: 2010-05-31
forum: Multimedia Software
---

### Post by izzi303 on 2010-05-31
Has anyone else been having issues with YouTube? I can watch videos but I can't adjust the volume, resize, pause, etc. I am using Chrome, Chromium, and Firefox.

---

### Post by tpho2500 on 2010-05-31
I too have this problem. Very annoying.

---

### Post by wilee-nilee on 2010-05-31
No problems here I think your probably missing some media stuff, not sure what that would be, but make sure you have the restricted extras installed in synaptic to begin with.

You could also have to many addon/plugins running in any of the browsers, but since it seems to be effecting all of them I would say that it is a missing media in the Ubuntu OS itself. A more specific description with each browser might get you the help you need if they react differently.

---

### Post by tpho2500 on 2010-05-31
I installed the ubuntu - restricted extras and I am still experiencing this issue.

Here's what happens:

When I click on a Youtube video it plays but nothing happens when I click on the pause button or on the video timelime (The red line and the slider). So I can't replay, fastfoward, etc.

I have installed Adobe Flash 10 from the official website and the Synaptics manager. 

Why is this happening and what should we do?

---

### Post by lovinglinux on 2010-05-31
That happens when you have the 32bit flash running on a 64bit browser.

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by tpho2500 on 2010-05-31
NVM, worked thanks

---

### Post by JustinR on 2010-05-31
I've had this issue for quite some time. I was using the Opera web browser, when I upgraded to the beta version the issue stopped completely, I have 64 bit flash installed.

---

