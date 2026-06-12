---
title: "Newbie's upgrade question"
date: 2009-11-15
forum: Mythbuntu
---

### Post by rbrown3 on 2009-11-15
Greetings:

   I currently am running Mythbuntu on Version 8.04 and would like to upgrade to Version 9. How can I do this without screwing up everything I currently have?

   Also: I am currently running my system using Hauppage PVR-350 cards. Are there any problems seen with that card under Version 9?

   Thanks in advance for any help...

---

### Post by rbrown3 on 2009-11-16
Folks:

  There is a good reason why I am asking this "newbie" question.

   I have gone to the main Mythbuntu site and have followed the links to the instructions for upgrading. Unfortunately, most of those instructions seem focused on upgrading from Version 9.04 to Version 9.10. Note please that I am running Version 8.

   There were instructions that were supposed to enable an upgrade from 8 to 9, involving the use of the Upgrade Manager. These instructions, which I followed to the letter, do not work. In running the Manager, I am supposed to see a message which says that Version 9 is available. As far as both the Upgrade Manager and my command line goes, I am "up to date" and there is nothing to upgrade to.

   That is why I am here now. Is there a way to upgrade from 8 to 9 while preserving my settings? If so, what is the proper procedure? Or am I going to have to destroy everything in order to install Version 9?

   Thanks in advance for any advice...

---

### Post by byronmyth on 2009-11-16
I'm pretty much a newbie myself, but the last upgrade that I did (9.04 -9.10) totally screwed my system. If you have the hardware spare I'd do a fresh install on a new drive, I've gone through the setup so many times now that I can get the system up and running from scratch in under an hour. Not ideal but the only way of knowing that you have a tight system. Just my take....

---

### Post by rbrown3 on 2009-11-16
Youch!

   This makes me a bit nervous. Do I really want Version 9.10???

   What happened to your system that it got so screwed up???

---

### Post by nickrout on 2009-11-16
you will have to do a number of updates e.g. to get to from 8.04 to 9.10 you have to go 8.04->8.10->9.04->9.10.

Glitches can occur in going through so many upgrades. You could use the weekly builds to get 0.22 on mythbuntu 8.04 

[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

### Post by dannyboy79 on 2009-11-16
if i were you i would follow mythtv website instructions on how to save out your database from mysql, then once it's saved on a flash drive or someone safe, just install 9.10 fresh, then follow instructions on importing your database. that's the safest bet. no mattter what, if you want to try to do the upgrade with 
sudo update-manager -d
i would still save you database off to a safe location.

---

### Post by rbrown3 on 2009-11-17
Thanks, folks, for the info.

   I will do the fresh install, possibly with a new machine (if I can afford to build one), after saving the database. I'll let folks know if I have any problems.

   I am, of course, a bit concerned about byronmyth's reply. I would still like to know exactly how 9.10 screwed up byronmyth's machine...

---

### Post by blackoper on 2009-11-17
I didn't have any problems with 9.10 and it actually improved my usability by finally making my hdpvr work in a stable way so.. there is a big currently with temperature logging that you may need to address. i hadn't noticed it yet but it's in the 9.04 to 9.10 upgrade thread that has a lot of pages

---

### Post by SiHa on 2009-11-18
> **nickrout] You could use the weekly builds to get 0.22 on mythbuntu 8.04[/QUOTE]

Kind of academic now, but incase someone stumbles across this:

[QUOTE=tgm4883 said:**
> MythTV 0.22 is not supported on 8.04. This is because the QT version in 8.04 is not high enough. You could try backporting QT, and then using a 8.10 package of MythTV 0.22, but thats pretty unsupported.

---

