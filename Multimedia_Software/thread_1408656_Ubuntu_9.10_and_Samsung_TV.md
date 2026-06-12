---
title: "Ubuntu 9.10 and Samsung TV"
date: 2010-02-16
forum: Multimedia Software
---

### Post by gj15987 on 2010-02-16
Hi all,

I installed Ubuntu 9.10 using my girlfriend's TV as a monitor and it all worked out fine. However, when I plug the PC into my own Samsung LE32R7 TV, I can't get a picture.

The TV kind of goes into a standby mode - like it knows there is some sort of signal present, but doesn't want to show the picture. If I turn the PC off, it then says "no signal found".

So, I plugged it into my brother's LG TV and got a picture, changed the resolution to 1360x768 and then plugged it back into my own TV - all working!

I restarted it a few times and it all worked great until yesterday when I unplugged the PC. I've not plugged it back in and am having my original problem.

So I mainly have 2 questions:

1. Does anyone know of a way to get a picture on my TV model?
2. Is there some sort of volatile memory storing my preferred resolution that gets lost when completely cutting the power?

Thanks in advance!

EDIT: Maybe I'm being thick and there is actually no Ubuntu problem but actually something wrong with the computer. I just used my brother's computer to switch the resolution to what my TV accepts, but on the first boot, I couldn't get a display! So I rebooted, and all of a sudden...a display!

---

### Post by andrewc6l on 2010-02-16
Samsung TVs are notorious for not working. You'll need to put a modeline in your xorg.conf file to tell it how to display.

Here's a link that has some useful info:
[http://www.mythtv.org/wiki/Modeline_Database](http://www.mythtv.org/wiki/Modeline_Database)

Here's a more general discussion on how to put a modeline in:
[http://howto-pages.org/ModeLines/](http://howto-pages.org/ModeLines/)

One more useful link:
[http://andrewmemory.wordpress.com/2009/10/25/modeline-for-samsung-ln32a450c/](http://andrewmemory.wordpress.com/2009/10/25/modeline-for-samsung-ln32a450c/)

---

