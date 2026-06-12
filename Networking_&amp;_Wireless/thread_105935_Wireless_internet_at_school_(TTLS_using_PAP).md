---
title: "Wireless internet at school (TTLS using PAP)"
date: 2005-12-19
forum: Networking &amp; Wireless
---

### Post by anil_robo on 2005-12-19
Hi all!
 
My school provides wireless internet in the entire building, and I am able to access it through windows XP. But I'd love to access it through Ubuntu as well, so that I can use Ubuntu at school as well.
 
The school IT department has written detailed instructions for configuration of wireless internet in [Windows XP ]("http://www.uth.tmc.edu/itsecurity/wireless/windowsWireless_XP.html")and [Apple Mac OS X]("http://http://www.uth.tmc.edu/itsecurity/wireless/airport/airportWireless.html"), but for Linux wireless setup, they just provide a link to [xsupplicant website]("http://www.open1x.org/").
 
I have installed xsupplicant and tried a lot of tweakings and settings in its configuration file but nothing works.
 
Can someone have a look at the procedure to setup wireless internet at my school on XP and OS X, and translate it into an Ubuntu script?
 
Any help would be much appreciated! I'll request the IT personnel to post such a script at the school website! :)

---

### Post by anil_robo on 2005-12-21
No one?

I tried to emulate the directions given for [apple computers]("http://http//www.uth.tmc.edu/itsecurity/wireless/airport/airportWireless.html"), but still it doesn't work! xsupplicant gives no error messages, but doesn't start the internet too! ](*,)

---

### Post by anil_robo on 2006-02-28
Quite some time has passed since I started this thread, and I have discovered some things myself.

1. Xsupplicant is something that I need to work with to get wireless internet at school working.
2. Xsupplicant is included in Ubuntu repositories, but does not work in its current installation state.
3. If you download and compile the latest xsupplicant from xsupplicant official website, that works for some reason. It's newer version, basically, that works.
4. I tried installing xsupplicant, and it wanted CRYPTO. I found the entire repos for crypto, but didn't get any package named crypto. So I installed something else... it was some tls crypto I guess... Still getting some dependency errors and unable to install xsupplicant.

Looks like I'll have to wait for Dapper to do the job for me. I hope they have included the working version in dapper repositories. Is there a way I can tell?

---

