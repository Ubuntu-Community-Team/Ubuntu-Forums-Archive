---
title: "DVD problem"
date: 2009-03-27
forum: Multimedia Software
---

### Post by grimm08 on 2009-03-27
I have not been able to play DVD's since installing Ubuntu.  This isn't a major problem since I have XP on the same computer.  When I put in the DVD the movie app said New Codec's are needed, I downloaded them and the Movie app does not play at all.  All other videos play fine such as .mpeg, .mov, etc.  If anyone can help I appreciate it.

---

### Post by aeiah on 2009-03-27
have a look at the sticky at the top of this multimedia & video section. i havent played a dvd in so long that i cant remember whether it installs it as smoothly as it does the avi codecs

---

### Post by Nero147 on 2009-03-27
The first thing I usually do when I do a fresh install of Ubuntu is install the restricted extras. This includes the mp3 and DVD codecs as well as flash and java and a couple of other things. Just remember to update your flash to 10. 

sudo apt-get install ubuntu-restricted-extras

Or you can install it from add/remove or synaptic if you enable multiverse and community maintained software. But this should fix your problem.

I also tend to use VLC to play movies because I can't stand Totem.

---

### Post by binbash on 2009-03-27
install libdvdcss2 from medibuntu repository

---

