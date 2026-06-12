---
title: "CTRL-ALT_F1 - blank screen problem"
date: 2006-02-18
forum: Multimedia &amp; Video
---

### Post by garybarwick on 2006-02-18
Hi 

I am using ubuntu 5.10 and have an ATI graphics card. I managed to get 1600x1200
resolution from the installation, but after having some flicker problems I followed the instructions on the wiki to install the fglrx driver.

Great!

However, whenever I use ctrl-alt-f1 etc. to start a new text-based login the screen blanks and I am unable to recover. I can't ++F7 back to gnome. I have cut the power to get the system back.

I am guessing it has something to do with the graphics card / driver / monitor.

Sometimes i get the message "DVI - can not display this mode" on screen when I switch. (this a monitor hardware message)

Any ideas?

Thanks

Gary Barwick

---

### Post by zi99y on 2006-02-18
I have the same problem using the latest fglrx driver (from the howto on this forum). Best thing you can do is use the 8.16.20 version that is included in the repos - works fine but you won't be able to use it with a later kernel version.

Hope someone finds a fix sometime soon as this is quite holding me back...

---

### Post by garybarwick on 2006-02-19
I have solved my problem, sort-of!

My monitor has two cables (digital vs analogue I assume). I have always used the newer digital cable. 

I swapped over to the old-style connections/cable and my problem has been solved.

This will do for me.

:)

---

### Post by zi99y on 2006-02-19
Glad you fixed it, strange that it works now though because the machine totally locks up usually and I wouldn't have thought using another monitor output would stop it crashing. But, if it works, it works!

I'm on a laptop so no such luck here :(

---

