---
title: "Forced to reinstall flash after every reboot"
date: 2010-05-03
forum: Multimedia Software
---

### Post by excelsior on 2010-05-03
Hi,
I have a bizarre flash-related bug. 

Every time I restart my computer, flash stops working. But once I reinstall flashplugin-installer, everything works fine.

Now it isn't too much of a hassle to reinstall flashplugin-installer every time I reboot (it takes 5 seconds, if that), but I was wondering if there was a way I could fix this minor problem.

---

### Post by no2498 on 2010-05-03
try this

sudo apt-get install ubuntu-restricted-extras

hope it helps

---

### Post by excelsior on 2010-05-03
It didnt work :(

I'm on 10.04 by the way.

---

### Post by excelsior on 2010-05-22
Solved it!

Apparently there was an old libflashplayer.so file in $HOME/.mozilla/plugins/

Once I deleted it, the problem was solved.

This is apparently a documented bug in 
[https://bugs.launchpad.net/bugs/532542](https://bugs.launchpad.net/bugs/532542)

---

### Post by XxBJDxX on 2010-06-25
i am having the same problem with my flash plugin, every time i restart it needed to be reinstalled, i have tried the fix mentioned in excelsior's link, hopefully it works, will report back with results.

---

### Post by XxBJDxX on 2010-06-27
still no luck, tried what excelsior mentioned, did not work for me, any suggestions?? ive tried some stuff off that bug report page, but to no avail

---

### Post by XxBJDxX on 2010-06-30
fixed, working now! :p

---

### Post by Vock on 2010-07-05
What did you end up doing? I'm having the same problem.

---

### Post by lidex on 2010-07-07
[http://ubuntuforums.org/showthread.php?t=1414595]("http://ubuntuforums.org/showthread.php?t=1414595")
[http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html")

---

### Post by Vock on 2010-07-08
Tried that, unfortunately didn't work. I actually tried installing the 64-bit version of Adobe tools and it Seg faulted. The 32 bit version worked, but it wouldn't install Adobe AIR.

---

### Post by lidex on 2010-07-10
Try this then:
[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html]("http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html")

---

### Post by Vock on 2010-07-13
Sorry, it's only happening on my work computer, didn't get a chance to try it out until now, giving it a shot. Thanks for the continued help.

Edit: Tried it, again it worked great until I rebooted, and then after reboot Flash stopped working until I reinstalled it again. This is weird and mildly annoying.

---

