---
title: "Completely Remove Mythtv"
date: 2011-09-14
forum: Mythbuntu
---

### Post by markackerman8@gmail.com on 2011-09-14
To Completely remove Mythtv and re-install it, and yes use synaptic or purge commands, but that alone is not enough ... 

you need to also remove all contents in:

/usr/share/mythtv
/home/myhtv
/var/lib/mysql/mythconverg/ or simply /var/lib/mysql
/var/lib/mythtv

reinstall
Done Solved

It has helped me a few times and again today so I thought I would throw it out there as I know a lot of people need this and it isn't easily googable, until now

---

### Post by nickrout on 2011-09-15
Oh good idea, remove ALL your mysql databases!!

---

### Post by tgm4883 on 2011-09-16
Why do you need to do that to "completely" remove MythTV if you are just going to reinstall it? How about you fix whatever is wrong the correct way instead of some half-brain reinstall & pray?

---

### Post by markackerman8@gmail.com on 2011-09-17
> **tgm4883 said:**
> Why do you need to do that to "completely" remove MythTV if you are just going to reinstall it? How about you fix whatever is wrong the correct way instead of some half-brain reinstall & pray?

I DEFINITELY like your troubleshooting philosophy, and try to work by finding the problem to learn from it, BUT, re-installing (mythtv, or ubuntu, or any EASY re-install) is often a great time consuming solution, ESPECIALLY when you have been pulling your hair out for MONTHS!  When a solution comes from it, that alone is somewhat helpful for diagnosing out the origional problem.

Your point however, is a good one and quite well taken:D, thanks,

Mark

---

### Post by Ubu_Fester on 2012-09-24
FWIW, the OP's instructions were to delete all the contents of the mentioned folders.  I didn't do that -- I removed all the contents and the folders.  Subsequently, my reinstall of mythtv (through the software manager of mythbuntu) was a complete failure -- I can't tell you exactly what happened but I was unable to get into the backend or frontend.

Only fix I saw was a complete reinstall of 12.04 (mythbuntu) which then created a fresh mythtv install -- and a clean database.  This was a mixed blessing.  While it was more work, my system is now up and running very smoothly so far.  

Now I just have to find a way to create a "recover" dvd so I can always "get back" to this pristine state.

---

