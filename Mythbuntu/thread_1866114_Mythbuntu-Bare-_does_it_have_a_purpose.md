---
title: "Mythbuntu-Bare- does it have a purpose?"
date: 2011-10-21
forum: Mythbuntu
---

### Post by GuiGuy on 2011-10-21
The mythbuntu CP has what seems like a backup utility called mythbuntu bare.

What is its purpose? What is it supposed to do?

I thought it might be intended to backup a mythbuntu system, such as configuration files etc and, by checking the box, back up the database as well. 

Clearly not, however. All I get is a couple of files (about 7K) from the home directory and some stuff from the /temp directory. 

Can someone enlighten me?

Thanks.

---

### Post by tgm4883 on 2011-10-21
> **GuiGuy said:**
> The mythbuntu CP has what seems like a backup utility called mythbuntu bare.

What is its purpose? What is it supposed to do?

I thought it might be intended to backup a mythbuntu system, such as configuration files etc and, by checking the box, back up the database as well. 

Clearly not, however. All I get is a couple of files (about 7K) from the home directory and some stuff from the /temp directory. 

Can someone enlighten me?

Thanks.

It is the backup and restore utility. I haven't looked at the code in a bit as I've been busy (and I still need to do documentation), but it should backup the database if you have checked that box, so it sounds like it is failing there. What version of mythbuntu are you using?

---

### Post by GuiGuy on 2011-10-21
> **tgm4883 said:**
> It is the backup and restore utility. I haven't looked at the code in a bit as I've been busy (and I still need to do documentation), but it should backup the database if you have checked that box, so it sounds like it is failing there. What version of mythbuntu are you using?

Hi,
I was using 11.04 but upgraded to 11.10 yesterday. WHich is why I was looking for backup options. It remains a great failing of Linux generally that there isn't an easy to use, reliable and intuitive backup solution (IMO).
 
 Lots of problems with the upgrade, which I have now mostly overcome except that the Control Panel (CP) now hangs if an attempt is made to apply an action that requires authentication. So it's all rather academic for the moment because the CP doesn't work. 

Working on it...

<sigh>

---

### Post by tgm4883 on 2011-10-21
> **GuiGuy said:**
> Hi,
I was using 11.04 but upgraded to 11.10 yesterday. WHich is why I was looking for backup options. It remains a great failing of Linux generally that there isn't an easy to use, reliable and intuitive backup solution (IMO).
 
 Lots of problems with the upgrade, which I have now mostly overcome except that the Control Panel (CP) now hangs if an attempt is made to apply an action that requires authentication. So it's all rather academic for the moment because the CP doesn't work. 

Working on it...

<sigh>

Hmm, ok so it could be that the CP isn't working properly, although there was a bug in earlier versions that didn't backup the DB. I plan on working on the documentation during my flight to UDS, so hopefully I'll have something helpful by then. There could also be bugs in the 11.10 shipping build, as there was a lot of political tug-o-war getting it into the repos which cut down on my bug squashing time.

---

### Post by GuiGuy on 2011-10-21
> **tgm4883 said:**
> Hmm, ok so it could be that the CP isn't working properly, although there was a bug in earlier versions that didn't backup the DB. I plan on working on the documentation during my flight to UDS, so hopefully I'll have something helpful by then. There could also be bugs in the 11.10 shipping build, as there was a lot of political tug-o-war getting it into the repos which cut down on my bug squashing time.

I have just done a clean install of 11.10 on the same hardware (swapped hard disks). Mythbuntu-bare and CP are working fine, so I suspect something got corrupted when upgrading. The thing is, of course, that the upgraded system was pretty well sorted in 11.04. 

That said I took manual backups before the upgrade so I might try and restore system and settings data to the new install and will see what happens. I'll keep you posted.

PS: Forgot to mention; in 11.04 mythbuntu-bare would not back up the database. On the new install it does.

---

### Post by GuiGuy on 2011-10-29
> **tgm4883 said:**
> Hmm, ok so it could be that the CP isn't working properly,

Only if I remove mythbuntu-bare. See [this thread...]("http://ubuntuforums.org/showthread.php?p=11407409#post11407409")

---

