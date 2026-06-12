---
title: "IBM T400 with Intel Mobile 4 Chipset and ATI Radeon 3400HD"
date: 2009-08-06
forum: Multimedia Software
---

### Post by Infin1ty on 2009-08-06
I was struggling for a few days with installing the radeon card, i tried almost any tuturial and guidance i could find (including this forum and the ati wiki) but i could not find a sulution to my problem.
so it goes like this:
This laptop has 2 graphic cards, one is the intel integrated and the other one is the radeon which i want to use on my ubuntu (9.04) at first back in windows i noticed that sometimes my whole background changes and then ask for "new hardware installation" after reboot. 
i kinda ignored that until i switched to ubuntu on that machine (dual boot) and then i realized what happened.
when i load the computer (after shutdown or restart) sometimes it prefers to use the intel graphic card as the default one and sometimes the ati.
in windows i found a nice way to force the system to use the ati only, i simply disabled the intel display card in the device manager and that solved the problems.
with ubuntu (linux) i find it very hard to do it, i also tried to blacklist the intel display card in modprobe.d but it didn't work out.
what i did notice is that sometimes when i restart or when i go into windows and restart and load ubuntu is that the intel graphic card won't show at all in lspci and only the ATI shows and at that point it's all working.... until the next reboot when lspci shows both and i can't load X.
 
The first time when i actually was able to use the ati card happened when i undocked the laptop from the docking station (no ac power connected at all) and then it loaded only the ati card.
but after a reboot the intel showed back as well, then i logged back into windows (worked a little bit there) and then reboot back into ubuntu and lspci showed only the ATI one.
 
I really think it has something to do with the power management because even though the ATI shows in lspci (with the intel one being first) and the fglrx module loaded!! (also aggart) i can't really access it and use it.
 
Is there a way to disable the intel one and use only the ATI? like the way windows handled it? (in a very dumb way i must add and that's why i really want to use linux)
 
 
Thanks.
 
[COLOR=red]**Anoter INPUT i forgot!**[/COLOR]

[COLOR=black]I now logged into windows again and even the ati stopped working (i guess it was just a way of luck), i searched a little bit more and i found out that if i want to use the ATI card it must first initialize at system boot which sometimes happens and sometimes not, the only way i guess is to go into the bios which right now i cant because the idiot who downgraded the VISTA (that came with the laptop) to XP thought it was funny to put a bios password and he can't remember it.[/COLOR]
If i won't find another solution (which i think i won't) i guess i will have to tell that guy to go to IBM and replace the motherboard at his cost. (this is what happens when you get a laptop from your workplace and you let those MS IT guys set it up)
 
[COLOR=red]Partially Solved[/COLOR]
[COLOR=black]If i want to reboot i first have to go into windows, be there for a few minutes and then restart back into linux, that way for some strange reason the intel card wont initialize at all, it's a temporary solution until i will have access to the bios password to set the ATI as the default card.[/COLOR]
 
So if anyone having problems not being able to configure their cards, first check that the card that you want to use is the one that get initialized first!! because if it won't intialize first you won't be able to use it.
 
now i just have to clean all the mess i have done with replacing the drivers and install a stable driver :)

---

### Post by samthehobbit on 2009-09-30
I've also got a T400 and had issues with the switchable graphics. I've configured the BIOS to use the discrete (ati) card. Also I've disabled OS switchable graphics. None of this helps you though if you can't get into the BIOS :o( 

What driver did you end up using? At the moment I'm using the open source driver which does 2D ok but no 3D - installing the ATI propriety drivers just leads to a system recovery ...

---

### Post by pawhtiobo on 2009-09-30
Hi :)
 
Changing the BIOS settings solved a similar problem here.
I can tell you that removing the password BIOS is a pain...last time that we needed to do that, here in the company we needed help of an external service, because de password is encrypted in the security chip, the old trick of removing the CMOS battery doesn't work anymore...it's better that your IT's take some pills for ther memory...loll
 
see ya...

---

### Post by samthehobbit on 2009-09-30
After posting I gave the latest ATI driver a shot (rev. 9.9 rel.9/9/2009) and hey presto I have 3D ... sweet.

---

