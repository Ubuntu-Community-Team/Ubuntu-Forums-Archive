---
title: "macromedia flash doesn't work, adobe says it's installed."
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by dsimpson on 2007-02-03
I know that this has been asked and written about dozens of times and solved in several different ways, but here we go again. I have tried all the different ways to install Macromedia flash 9 and it seems installed, I see it in .mozilla; plugins and components, it shows up in firefox, about:plugins, I went to Adobe website and it says it is installed on firefox, but still when I go to my library site for a language program that requires flash, it says I am missing plugins, I do the search for plugins and it doesn't find any, and asks if I want to manually install. I have done 2 different ways through the apt-get/terminal route, '**this**'([http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)) and an alternate way that was for Edgy and didn't work for me. I have downloaded it manually from the Adobe site and opened it and installed, and still come up with the same problem. I have closed firefox, rebooted, and still no change. I really need some new ideas here. :(

---

### Post by glabouni on 2007-02-03
I spent 2 hours at a friend's yesterday fixing this problem with win xp and IE. it seems flash plugin v9 is not always detected as adobe changed something.

you might want to try to reinstall flash using [automatix]("http://www.getautomatix.com/") or [ubuntuguide]("http://www.ubuntuguide.org/").

if this doesn't fix your problem, consider downgrading to flash 8.

---

### Post by dsimpson on 2007-02-03
Thank you, I cannot use automatix, it is not supported for Ubuntu 6.06 - Dapper. It is sure disappointing for this one thing to be the only annoying part of an otherwise great system. You cannot blame Linux though, we need better support from the software designers. I have it grayed out in EasyUbuntu so it cannot be done through there, I am running out of options other than to keep trying to install it manually through terminal. I have followed the directions on Ubuntu DapperGuide also.
Could my problem be, since it seems to detect Macromedia flash, not that at all, but a need for Shockwave instead? How would one go about detecting the exact missing plugins when they are both from the same site? :confused:

---

### Post by dsimpson on 2007-02-03
I checked around the site that I was attempting to log onto and found it did require ShockWave. I am unable to blame it on Flash any longer, so I guess that Adobe Flash is installed ok and I need to use Wine to play Shockwave media. I will mark this problem resolved.

---

### Post by Mets on 2007-02-03
Automatix works with Ubuntu 6.10, Ubuntu 6.06 and Mepis 6, so you should have no problems getting it to work.  You could always upgrade to 6.10 too.

Also, don't ever, ever, use EasyUbuntu, it's an absolutely terrible program.  Stick with Automatix.  Also, when you do get Flash working, install the extra fonts option as well.

---

### Post by towanda on 2007-02-25
I just got Flash installed and (apparently - knock wood) operating on a fresh Dapper install on an old 32-bit x86 machine.  Thing is, now I can't seem to get Shockwave working.  Does Shockwave run only under Wine?

---

