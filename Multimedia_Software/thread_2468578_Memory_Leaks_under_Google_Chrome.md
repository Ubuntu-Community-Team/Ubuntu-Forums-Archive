---
title: "Memory Leaks under Google Chrome"
date: 2021-11-03
forum: Multimedia Software
---

### Post by stevecoh1 on 2021-11-03
I am currently on Ubuntu 21.04. I have all the latest packages, including Google Chrome.

Back a couple of years ago, I paid no attention to memory usage which caused the computer to lock up, frequently.  To solve this problem, I installed the System Monitor with an indicator in the upper bar of the computer screen.  This worked very well, so when I see the Memory usage getting up around 7GB (my PC has 8GB), I close windows and browser tabs I no longer need, and I almost never have lockups anymore.  (and if I ever do, I have the Magic SysRq key to get me out of it).

For many years I used Firefox as my default browser and I find it reliable, albeit limited in some respects.  It won't show .pdf's when browsing which can get to be annoying.  I've started to look at switching to Google Chrome. It is more full-featured, albeit at a cost of more memory.  The problem is, it doesn't give back that memory when it is done. Running my computer with Ubuntu started and nothing running, the System Monitor Indicator shows me a constant 1.6GB of Ram usage.  If I run Firefox, open as many tabs as I want, then close Firefox and any other running apps, the index drops back to 1.6GB used. With Chrome though, it's a different story. If I open a few tabs in Chrome, then close it, I find myself with 2.4 or 2.5 GB used.  The process monitor shows no process with "google" or "chrome" in their name, but there's 0.8 or 0.9 GB of ram being wasted, only with Chrome, not Firefox.

There's a lot of generic content on the web about making browsers use less memory, but that's not my issue.  I want to know why Chrome is stealing my memory and not giving it back when it's done. Does anyone have any information specifically geared to this particular problem?

---

### Post by stevecoh1 on 2021-11-03
Mystery solved.  

Chrome offers a setting: "Continue running background apps when Google Chrome is closed" under Advanced->System.  Turning this off makes the problem go away.  So it's not really a memory leak, it's doing what the default settings tell it to do.

By the way, I'm pretty sure this forum is not the correct place for my question but I couldn't find the correct place.

---

