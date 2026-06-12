---
title: "Dual vid cards"
date: 2010-01-23
forum: Multimedia Software
---

### Post by Lostsouls on 2010-01-23
So i just made the switch to Ubuntu. And i face my first few problems. The biggest one being that i am a multi monitor guy. I have 3 monitors spaned over 2 cards. 1  22" on a ati 4870 and 2  17" on a ati 2400 pro.

The biggest problem ofc is that im comming from W7, sow im a spoiled guy. And i just can't figure out why after installing the ati 9.12 drivers following this guide ( [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) ) My 2400 pro shows up as an unknown card to catalyst control center ( see [http://i199.photobucket.com/albums/aa141/lostsouls1991/Screenshot-1.png](http://i199.photobucket.com/albums/aa141/lostsouls1991/Screenshot-1.png) )

I also uploaded my xorg config to : [http://rapidshare.com/files/339732244/Xorg.0.log.html](http://rapidshare.com/files/339732244/Xorg.0.log.html)

As you can see in the file the 2400 shows up in the config sow I'm a bit confused,

so any suggestions ?

Greetz

---

### Post by drdos2006 on 2010-01-23
Check out randr. It may help you.
regards
{edit]
Do a search on these forums first...
[/edit]

---

### Post by markbuntu on 2010-01-24
What you need to do is open the Catalyst Control Center as superuser and go to the display manager screen and drag the 'unknown card" into the box above. 

If the supresuser CCC does not open, which is a common problem, open a terminal and type

sudo amdcccle

this will ask for you password and once you type it in CCC will open. 

You need to be a little careful making changes with CCC, only one at a time and then reboot. I have two ati cards and three monitors and have had no problem getting them working. One thing though, you will not be able to use desktop effects (compiz) on more than one monitor due to xserver limitations. This should be fixed in the next distribution release.

---

