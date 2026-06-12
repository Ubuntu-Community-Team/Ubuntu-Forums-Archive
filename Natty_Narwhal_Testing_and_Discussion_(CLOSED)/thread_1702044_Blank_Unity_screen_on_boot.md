---
title: "Blank Unity screen on boot"
date: 2011-03-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ?#Yhf%*&amp; on 2011-03-07
I am using Ubuntu 11.04 Alpha 3, running on a Toshiba NB205 netbook. I made the USB drive bootable with the latest UNetBootin for Windows.

I commonly switch between Windows (on the internal HDD) and Ubuntu (on a 2 GB Live USB drive). About half of the time, Ubuntu takes a much longer time to boot up, and after it does, it simply displays a blank screen with nothing but the mouse (working) and the desktop image.

I have found that several re-boots and switching of USB ports on the netbook fixes the problem. After that, everything works. :confused:

Perhaps someone high up in the Ubuntu kingdom fix this? It's very annoying. :mad:

---

### Post by kerry_s on 2011-03-07
compiz crash's a lot in 11.04, leaving stuck like that.
i have gexec set for my run command(alt+f2) so i can run "compiz --replace" easily, but you can also just create a desktop launcher to click on.

---

### Post by ?#Yhf%*&amp; on 2011-03-07
I personally think that Compiz is not much better than Mutter. Mutter makes me shutter. :P

---

### Post by VMC on 2011-03-07
> **kerry_s said:**
> compiz crash's a lot in 11.04, leaving stuck like that.
i have gexec set for my run command(alt+f2) so i can run "compiz --replace" easily, but you can also just create a desktop launcher to click on.
I keep getting fatal error when I try that. Using "sudo service gdm restart" works for me.

---

### Post by kerry_s on 2011-03-07
> **VMC said:**
> I keep getting fatal error when I try that. Using "sudo service gdm restart" works for me.

sounds like your running it from a terminal.
install gexec & do a keyboard shortcut, if you use alt+f2 you need to disable the stock, which doesn't work anyways.

---

### Post by VMC on 2011-03-07
> **kerry_s said:**
> sounds like your running it from a terminal.
install gexec & do a keyboard shortcut, if you use alt+f2 you need to disable the stock, which doesn't work anyways.
Works great, thanks! I tried some other one but it didn't work right.

---

