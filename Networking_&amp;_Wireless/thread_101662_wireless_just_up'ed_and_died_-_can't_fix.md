---
title: "wireless just up'ed and died - can't fix"
date: 2005-12-10
forum: Networking &amp; Wireless
---

### Post by harty83 on 2005-12-10
Okay so the craziest thing happened yesterday; off of a sudden, my wireless stopped working.  I have a broadcom card that uses the bcmwl5 driver (installed through ndiswrapper).  

Ubuntu is recongizing the card.  The card is active under Network Settings and is configured properly.  But, I can't get it to connect to my network.  

I have tried uninstalling completely ndiswrapper and recompiling from the latest version (1.7).  I have tried reinstalling wireless-tools just for the hell of it.  Last night I even upgraded to Dapper (I enjoy the challenge) but have the same problems.  I've tried to connect to the network through the terminal but when I type "iwlist wlan0 scan" my network doesn't even show up.  

And yes, my wireless network is up and running b/c my wife is able to connect (through a winblows machine).  

All the .conf files in /etc/ndiswrapper/bcmwl5/, RadioState are all set to 1.

Ideas anyone?

Alan

---

### Post by Swab on 2005-12-10
Perhaps the wireless card is actually broken.  Why not try it in another machine... or try it in another PCI / PCMCIA slot?

---

### Post by tabinin on 2005-12-10
Some thing happened to me with an IOgear PCMCIA card.  Just croaked one day.  I am guessing it was from overheating, as it is warm when I took it ou

---

### Post by harty83 on 2005-12-10
Its an internal truemobile wireless card installed in a dell inspiron 5150.  Testing it on another machine won't be easy :-)  

I'll test it using a live cd just to see if it is a file somewhere that is jacked up.

Sigh, you may be right...I can't get it to work in even using a live cd...same problems. 

I'll pull the thing apart and check the physical card itself and attach it else where if possible

---

### Post by harty83 on 2005-12-10
Okay so it is NOT the card itself.  I was able to put it in my wife's laptop (running windows xp) and it worked fine.  

Any more clues?

---

### Post by harty83 on 2005-12-10
well blow me down and pick me up my wireless card lives!  Well, just as weird as it was for it up and die, its just as weird for it to up and live.  Not a clue what happened.  I reinserted the card and had the same issue.  But, I again uninstalled the driver (through ndiswrapper) and resintalled it (just like I did before) and wola...it works now.  Oh, well not complaining.  I was planning on having to buy a new card!

---

