---
title: "WUSB11 v2.8 Lucid Lynx"
date: 2010-07-07
forum: Networking &amp; Wireless
---

### Post by cre8ive65 on 2010-07-07
HI
i have a linksys wusb11 v2.8 and i have just moved from machinimating on windows 7 to ubuntu. i have tried everything to get this card to work, and every where i've checked, the card is "green light" and is compatible but i just cant get it to work. Ive tried ndiswrapper and the other linux driver methods. ndiswrapper has the right driver, but cant recognize the device, and when i try it the way the ubuntu site told me to with the CVS thingy, the packages build-essential, and CVS can't be found. i need the internet on this computer for machinima and i am a coplete newbie, i just switched yesterday so go easy on me ;)

---

### Post by roosh on 2010-07-07
When installing the packages, you need to be connected to the internet; that could be your problem.

Also, can you open a terminal and post the output of:
```
lsusb
```
```
lspci
```
and
```
lsmod
```

---

### Post by Jurgen Oscar on 2010-07-08
hello cre8ive65,

Save your breath and effort.

Do not try anything else, just buy a new card.

I had tried so many avenues...NOT WORKING.

So, it's up to you man.

J.O.

---

### Post by roosh on 2010-07-08
> **Jurgen Oscar said:**
> hello cre8ive65,

Save your breath and effort.

Do not try anything else, just buy a new card.

I had tried so many avenues...NOT WORKING.

So, it's up to you man.

J.O.

Did you try ndiswrapper with XP drivers?

---

### Post by bkratz on 2010-07-08
You might also want to look at this thread.

[http://ubuntuforums.org/showthread.php?p=9306475](http://ubuntuforums.org/showthread.php?p=9306475)

---

### Post by cre8ive65 on 2010-07-19
Thanks a ton for your time and effort
after many wasted hours, i order a cheap sweatshop chinese adapter, $12.99 CAD and it worked out of the box, thank everyone

---

