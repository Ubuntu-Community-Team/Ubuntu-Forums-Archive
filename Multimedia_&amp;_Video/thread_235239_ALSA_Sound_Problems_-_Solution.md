---
title: "ALSA Sound Problems - Solution"
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by Tyche on 2006-08-12
:D I SUGGEST THAT THIS BE MADE A STICKY

I have finally resolved my sound-card problems, and offer this solution to others with the same "no sound" problem I have had. ](*,) 

Aparently, Ubuntu does not completely install Alsa, nor the sound devices necessary to operate the sound card.  Instead, go to

[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

Look up the sound card for your system by manufacturer (i.e. Creative Labs) to see if it is supported.  This will take you to a page with the supported sound cards for that manufacturer listed.  It will list the chipset and the driver.  Click on the driver will take you to a page describing how to configure, make and install the Alsa drivers.  Download the suggested files (use a second window/browser for this, so you can keep the instructions up).

SUGGESTION:  To follow the directions, open a root terminal, or a standard one and log in as root (alternatively, you would have to preceed their instructions with sudo)

At the end of the directions, where it says to open alsamixer and adjust as necessary, you STILL may not be able to do so (the system may still not be able to find your sound card).  RE-BOOT, and you should be able to open alsamixer.

BTW:  I am NOT an expert in Linux, and don't know all the answers.  I found this solution more by accident born of desperation than anything else, and it has taken me a number of months to find.  If you have tried other solutions and have been unsuccessful, try this.

Craig
(Tyche)

---

