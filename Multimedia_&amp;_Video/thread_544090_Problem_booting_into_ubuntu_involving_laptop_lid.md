---
title: "Problem booting into ubuntu involving laptop lid"
date: 2007-09-05
forum: Multimedia &amp; Video
---

### Post by Faluzure on 2007-09-05
I am posting here, because I am pretty sure that the problem involved the graphical user interface, or graphics driver.

When I start ubuntu with my laptop's lid open, it will get halfway done load and crash and tell me that XWindow is unable to continue loading, and kicks me to the command prompt. However, if I load all the way into ubuntu when the lid is closed, ie there is no display being generated, it works flawlessly, and I can log in and mess with the GUI like normal. 

Any ideas? This problem is really weirding me out.

Other information you guys might find useful.

I get the same sort of error when I tried to install using the LiveCD, except it ends with the "/bin/sh: can't access tty; job control turned off" error. So I did the install with the text based CD, which went flawlessly.

I have an LG R405 notebook based on the 965 chipset, with integrated X3100 graphics.

Thanks
-Joe

---

### Post by mocoloco on 2007-09-05
Not sure, but one thing you can try is to turn off the bootsplash.
```
gksudo gedit /boot/grub/menu.lst
```
Find the line near the bottom that launches Ubuntu, in the section above the one that says recovery mode.  There's a line that ends with "splash".  Take out the word splash (remember where it was), save, and reboot.  See if that's causing it.
This is strange, happening before X starts.

---

