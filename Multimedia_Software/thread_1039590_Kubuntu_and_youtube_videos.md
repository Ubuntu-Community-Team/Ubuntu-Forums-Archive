---
title: "Kubuntu and youtube videos"
date: 2009-01-14
forum: Multimedia Software
---

### Post by wayreth on 2009-01-14
Hello there.

I apologize if this has been asked before, but I was unable to find a solution.

Anyway, here's the problem: I've just finished installing Kubuntu 8.04 and am very happy with it, for the most part. However, I can't watch youtube videos, either via konqueror or firefox. It always asks me to get the latest version of adobe flash player.

Well, I did, but it still shows the same message (I restarted the system, just to be on the safe side).

Adept manager tells me I have the following packages installed:
adobe-flashplugin
flashplugin-nonfree

What else do I need? 
Can you provide me with konsole commands from scratch?

Please don't go all mumbo-jumbo on me; I'm still learning the ropes here! 

Thanks.

---

### Post by stefangr1 on 2009-01-14
I heard about this a few times before. What you can try is:
(1) uninstall flash
(2) delete ~/.mozilla/firefox/*.default/xpti.dat
(3) go to the adobe site and download the latest version of flash from there

---

### Post by binbash on 2009-01-15
can you see the flash plugin after entering about:plugins to firefox?

---

### Post by wayreth on 2009-01-18
I had to reinstall Kubuntu. I downloaded Firefox again and the adobe flash plugin as well. I manually installed and it's now working fine.
Thanks guys.

---

