---
title: "Realtek 8187 driver problems!"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by Henery on 2009-02-24
I am having trouble getting this modded driver to work hxxp://ubuntuforums.org/archive/index.php/t-963923.html 
I can get the standard driver to work but I want this one as it supports packet injection! I can compile it and install it and all goes well till the last step when I reboot it fires up and the _driver is activated but not currently in use!_ I don't know how to get it to start on boot! 
I am a noob so go easy lol!

---

### Post by Henery on 2009-02-25
A friend of mine has this same card working with these drivers on another machine!
We can't get it to work on this lappy though there must be a command I can type in terminal to get this to be in use!
I had the same trouble with my on board card this was the command I used to fix it.
echo wl|sudo tee -a /etc/modules this is what fixed my Broadcom card Maybe the same can be done with the realtek card?

---

### Post by Henery on 2009-03-09
Well my problem was a compiling error all good now anyway!

---

