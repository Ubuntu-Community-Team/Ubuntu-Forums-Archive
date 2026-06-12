---
title: "Does any distro work with my ATI card?"
date: 2007-12-15
forum: Multimedia &amp; Video
---

### Post by mjpolifka on 2007-12-15
I have an ATI Radeon X1650 PRO.  It's a pretty bitchin card considering the deal I got on it (half off), 512MB dual 400MHz GPU's, all for around $50.  I really don't want to have to buy a new card, especially since I'll probably be upgrading to a dual-core box within the next year, which means no more AGP and yet another new video card.  This is the single problem I have with Linux, if it weren't for a lack of WoW I would ditch Windows entirely and never look back!  My friend recently bought an NVIDIA card and WoW works great on his machine, so I know this can be done.

I have tried to install the ATI drivers every possible way, on both Fiesty and Gutsy, and three different releases of the ATI driver, each of which promised to actually work, but have never been successful.

I was thinking maybe this was a problem with either Ubuntu or Gnome (I was thinking of trying KUbuntu before anything else, I love Ubuntu!), but before I try any other distros I thought I would ask if anyone has had success either with this card, or with a different one on another distro (if it's a different one, it has to have not worked in Ubuntu or in Gnome and then did work with another distro).

Don't get me wrong, I'm not complaining about Ubuntu, nor would I ever leave you guys (my laptop and one of my servers run Fiesty, the other server runs Debian due to low resources).  But I think you can agree that using a different Linux distro is certainly better than using Windows!  This post got long quick, so thanks for sticking around, and thank you for any information at all that might help.

---

### Post by kajillin on 2007-12-15
hey,

could you give more info on whats happening, i can almost guarantee that you hardware will work with some tweaks. so maybe explain whats happening and at which point, which driver your using, and any changes youve made to the config. I have a x1650 on one of my other machines and it works with ubuntu just fine.

Cheers,

---

### Post by Auax on 2007-12-15
My other laptop has an X1650 PRO, and sudo apt-get install fglrx worked fine for me.

---

### Post by mjpolifka on 2007-12-15
It's been a few weeks since I've done anything, but I'll work on that today and provide some more information.  What I do know, is that I used this HOW-TO: [LINK]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide"), and did it both through apt and the manual way.  I just tried the apt way again and it says all those packages are the latest versions, but when i run fglrxinfo it says my driver is Mesa.  Also, when I run glxinfo | grep direct, it says direct rendering: no (which I expected with the mesa driver).  In a little while I'll try installing it the manual way and let you know what the problems are.  Later on I'll also try a fresh Gutsy or Fiesty install (whichever you think would be better, Gutsy wasn't an improvement for what I use it for so I wouldn't mind going back) and try both methods again.

The last time I tried the manual way, i remember fglrxinfo coming up with the correct values, and glxgears running at about 4k fps (i think).  But I don't beleive glxinfo came up with direct rendering:yes, and I beleive when i restarted my computer it went back to the mesa driver.  The right driver might still be installed, but for some reason on restart it reverted to mesa.

For those of you who had success with this card, have you used it for any games?  Remember, my goal here is to play WoW.

Also, my system:
Unknown Intel Motherboard (any way to find that out in lInux?  windows doesn't really recognize it)
P4, 2.8GHz
2.5GB memory (forgot what speed)
ATI Radeon X1650 PRO AGP graphics card

Anything else you need, just ask.  Thanks for the help.

---

