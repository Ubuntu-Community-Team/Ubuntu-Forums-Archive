---
title: "MCE Remote doesn't work with front end"
date: 2010-03-12
forum: Mythbuntu
---

### Post by jreiner3 on 2010-03-12
I have a Pinnacle MCE Remote, I set lirc to work with all Windows MCE remotes. When I run irw I get feedback on the screen that corresponds to the buttons I've pushed, but when I start the mythTV front end the remote does not work. Am I missing something obvious? I can post configuration files but I have not configured anything outside of the options in Mythbuntu.

---

### Post by jreiner3 on 2010-03-12
The remote is working in the front end now. 

I wish I could say what I did that made it worked but I think that would require me knowing what I did (or didnt do) to make it not work in the first place. Long story short after trying everything I could find online regarding mce remotes I decided to start over. Set the remote to All Windows remotes in the IR section of the Control Center. lircd start, irw works, started the front end and the remote worked. Think I made it way harder than it has to be.

I am building this on a Zotac MAG HD-ND01 NVIDIA ION mini system, with a dual core Intel Atom 330 processor and NVIDIA ION graphics. I will do a complete write up on hardware specs once I get everything working and wife friendly.

---

### Post by necochino on 2010-03-19
I have a Zotac MAG with Linux Mint (Karmic) and XBMC.  I have been trying to get my LIRC to work for the last 2 weeks without success (only sporadically).  I have a PCTV USB (not the pro).  I wonder if this is defective.  Have you figured out how you got Lirc to work?  Cheers,

---

