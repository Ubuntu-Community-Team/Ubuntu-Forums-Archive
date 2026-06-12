---
title: "ubuntu server 12.04 problem with tp-link tl-wn422g"
date: 2013-04-03
forum: Networking &amp; Wireless
---

### Post by navoye on 2013-04-03
hello,
I'm gettin trouble with wifi adaptor. Generaly works fine during install, but i'm getting trouble when i rebot my machine - sometimes it works ok, sometimes im getting error (waiting for network configuration) during boot. If i get error nothing can help me (get dongle out and put it in, restart network and other things i find on google) - the only way to get wifi back is reboot few times, sometimes power down and power up - no regule.

what's my system - Ubuntu server 12.04(kernel 3.2) with openbox and  lightdm for automatic login(if it will help i can write exacly how i  bulid my enviroment)
What i trying to get - flaviously working wifi dongle without truble, next step is to manage it from network manager with gnome applet and tint2 as a taskbar.
what i try so far - changed router, changed machine, changed wifi security on router, do a clean instal (im learning so sometime i leave a mess and i'm not sure how to tidy :)
whats my skill - i'm a beginner - step by step instruction will be nice, if You have time for coments it will be great - it will help me to understand and learn.

If You have idea - please help.

---

### Post by agent-squirrel on 2013-04-03
Sounds like the driver is buggy and not hotplugging correctly, I beleive a few other Atheros based cards have this issue.
It may pay to look up your exact chipset and see if Atheros provide an open source driver to install?

---

### Post by navoye on 2013-04-04
hmm, i will be searching it(but first i must read about it :) ) - ubuntu use ath9k_htc, i didn't install any driver manualy


-------------------------------------------
i find that it's standart this wifi dongle issue

---

