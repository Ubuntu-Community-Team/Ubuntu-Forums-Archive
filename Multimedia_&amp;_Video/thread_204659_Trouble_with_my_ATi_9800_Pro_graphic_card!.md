---
title: "Trouble with my ATi 9800 Pro graphic card!"
date: 2006-06-27
forum: Multimedia &amp; Video
---

### Post by kizz on 2006-06-27
Hi!

I have an Ati graphic card and want to install ATI drivers for it. I have tried to install with easy ubuntu, tried to follow the "howto Ati guide" and got a lot of help with Lamega, Famous and Snoops on Irc. (#ubuntu)

I have tried to install with easy ubuntu on a clean ubuntu (just installed), and I have tried to install from the howto on a clean ubuntu. I tried the howto twice, both times on a clean install of ubuntu. (I have installed ubuntu 4 times in 2 days). 

The problem is that the Mesa driver want's to drive my graphic card, I think. Everytime after checking glxinfo, the Mesa driver is enabled. 
I don't get any errors or something like that. The pc works fine...

Now I'm asking you guys, to help me. Send me links, hints, tricks or whatever, I'm not able to fix this problem myself :P

---

### Post by Steven_B on 2006-06-27
Which version of the fglrx drivers are you using?
Are there any "EE"s in your Xorg.0.log (/var/log/Xorg.0.log)
If so, could you post those lines?
Also, what is the output from:
```
dmesg | grep fglrx
```
From what I understand, mesa takes over if the card's 3d acceleration doesn't work.  I'm pretty sure it's a matter of getting the fglrx driver to work properly, not disabling mesa.

---

