---
title: "Ati's drivers pisses me off"
date: 2006-05-19
forum: Multimedia &amp; Video
---

### Post by Cene on 2006-05-19
First of all, sorry for the bad english, it's not my main language.

I've been using Linux for few months now.
Everything worked fine for some time, then my computer just froze up. Nothing worked except mouse. It happened always on reboot, when gdm was supposed to start. 
I could not find any solution for this problem, and I reinstalled Ubuntu. Everything was fine, except I was stuck on Mesa drivers, no matter what I did. Mesa just stayed there. ](*,) 

After that I had hard drive failure, and had to reinstall everything, still no luck with drivers.
Now I can get Breezy's included fglrx drivers enabled, but the whole computer freezes about 30 secs after I log in, at the "Restoring session" or soon after it (I'm using KDE nowadays), but never on the login screen. Everything else is frosen except I can move the mouse. Only thing that works is to press ctrl+alt+f1 before logging in and change drivers back to Mesa with dpkg-reconfigure.

Ati's own drivers just gives me shit (sorry, I couldn't find better word) to screen, like the resolution or refresh rate were too high/unsupported, and it freezes at same point as Breezy's own drivers. I have tried chancing both from xorg.conf and with aticonfig with no luck.

In both cases, I could not find any critical errors from Xorg.0.log.

Well, back to Breezy's own drivers. I think the problem is in fonts (is that possible?).
Only errors I could find from Xorg.0.log was referring to fonts not found, and the menus on the login screen looks weird, and fonts are unclear.

I'm running 32bit Breezy at Athlon XP 2800+, 512mb RAM, Radeon 9600, Some Abit motherboard with nForce2 and k7-smp kernel.

My Xorg.0.log is too long to this post and too long for pastebin, so I put it to Rapidshare:
[http://rapidshare.de/files/20845629/Xorg.0.log.html](http://rapidshare.de/files/20845629/Xorg.0.log.html)

Please help me. :???:

---

### Post by tribaal on 2006-05-19
I know it might not really be the answer you expect, but yeah, ATI drivers suck (for the time being).

You're probably aware that ATI drivers are not open source, so the drivers you use are coded by reverse-engineering, which is a long, tendious process. 
A little thought for the crazy coders that work on this crazy project ](*,) 

Something you might want to consider is to upgrade to dapper, as I believe the drivers are better integrated (via the linux-restricted-drivers package, in Dapper's Universe reps). Dapper is really stable now (it's almost released), so you probably don't take much of a risk installing it instead of breezy. 
Also, make sure you build a separate /home partition (it's an option in the install menu), so reverting to breezy if something funny happends will be much easier, and you won't loose all your personal data and files...

Good luck with ATI :(

- trib'

---

### Post by Cene on 2006-05-19
Yeah, well, the only thing that keeps me in Breezy is that I'm really worried at apt-get dist-upgrade. Last time I tried upgrading, the result was that my computer crashed during it and I needed to reinstall.

Well, I have to think about that.

---

### Post by ZiLOG_Z80 on 2006-05-19
[QUOTE=Cene]I'm running 32bit Breezy at Athlon XP 2800+, 512mb RAM, Radeon 9600, Some Abit motherboard with nForce2 and k7-smp kernel.[/QUOTE]

I dont know if this will have any affect on the problem you have but i couldnt help noticing you have the k7-smp kernel which is for multiple processors. there is a none smp version for single processors

I have the k7 kernel and am running the ati driver no problem

---

### Post by Cene on 2006-05-19
[QUOTE=ZiLOG_Z80]I dont know if this will have any affect on the problem you have but i couldnt help noticing you have the k7-smp kernel which is for multiple processors. there is a none smp version for single processors

I have the k7 kernel and am running the ati driver no problem[/QUOTE]

Oh, is that so? Someone said to me that k7-smp would be the most suitable kernel for my comp.
Well, I'll try with k7 kernel. Thanks for the info.

---

### Post by Cene on 2006-05-19
Okay, I tried with k7 kernel, and everything works smoothier, but still no help to driver problem.

---

### Post by Cene on 2006-05-27
I upgraded to Dapper with dist-upgrade, this time no problems at upgrading.
Now the computer freezes even with Ubuntu's own Ati drivers, and I'll have to use vesa. :|
But it's not a problem, I ordered a new nVidia card today, it'll be arriving within a week.

Thanks to everyone who tried to help. This problem is now history.

---

