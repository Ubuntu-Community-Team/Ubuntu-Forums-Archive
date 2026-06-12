---
title: "Monitor problem 8.04"
date: 2008-07-22
forum: Multimedia Software
---

### Post by AB34125 on 2008-07-22
hi guys, 

Having some problems here.

Just hooked up a new monitor to my computer.  Went to change the screen resolution.  after clicking on the differnt resolution settings it came up with 'keep settings'  though there was no change.  I then restarted the computer and I cant get a piture.  

I can click on Alt-Ctrl-f1 and getting in to prompt.

is there a way to force resoultion atleast get me back up and running.

I have a Dell SX270 connected to an acer AL2216W monitor.  

If I could just get it back up to how it was when i first turned it on would be enough.

thanks in advance.

---

### Post by AB34125 on 2008-07-22
I have tried to reconfigure x xerver by using the follwing comands

sudo dpkg-reconfigure -phigh xserver-xorg

and

sudo dpkg-reconfigure xserver-xorg

but neither of these have helped.  when I get the blue dos type screen up and it asked me setting details it is only about the keyboard nothing about the monitor resolution or settings.

---

### Post by xc3RnbFO8P on 2008-07-24
Try,
atl+f2
> gksudo displayconfig-gtk
Choose Generic
and resolution that your monitor supports

---

