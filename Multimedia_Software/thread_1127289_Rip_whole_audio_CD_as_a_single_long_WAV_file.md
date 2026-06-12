---
title: "Rip whole audio CD as a single long WAV file?"
date: 2009-04-16
forum: Multimedia Software
---

### Post by Pipps on 2009-04-16
Is there any readily accessible software in the repositories which will perform the function of ripping an audio CD to a single long WAV file, rather than ripping the whole CD track by track?

I've tried Grip as a ripper, but it does not have this option.

I've tried to install Ruby Ripper, but I've had no success and found no complete guidance on the subject.

Can anyone help please?

---

### Post by SuperSonic4 on 2009-04-16
k3b does it, if you click on "Start Ripping" and select wav from the menu on the left it should have a box on the right saying "Create Single File". If you tick that box and click start ripping it rips to one long file

I will look into using cdparanoia for a cli option although there will be no cddb entry

---

### Post by Pipps on 2009-04-16
Thank you, fellow Brit!

This is brilliant! :D

---

### Post by SuperSonic4 on 2009-04-16
Seems it can also make a cue file for easy burning back to cd (which I didn't know until now so thank you for that xD)

I don't seem to be having much luck with cdparanoia >.< although I think it's because it insists on using /dev/sr0 instead of /dev/sr1

edit 2: It seems to work as root but not as user. I suspect it's because root owns the disc so to speak (but I can use k3b as user)

```
sudo cdparanoia -d /dev/sr1 -v 1-11
``` 
where 1-11 is all the tracks, 
-d forces the use of /dev/sr1 (you probably won't need it if you only have one cd drive)
-v is verbose mode

it's ripping for now, not as quickly as k3b but the output says it's ok



unless of course using cdparanoia is superfluous to your needs, k3b is rather easier XD

---

### Post by ajgreeny on 2009-04-16
If you have already got separate tracks you can easily amalgamate them with **mp3wrap**, a command line app, but very easy to use, and it does it all without decoding and then re-encoding, so there is no quality reduction.

Also look at **mp3splt** and **mp3gain**, great tools for managing mp3 files.  Now you will be able to wrap files or split them (by time or silences) and amplify them if needed, with just a single line of simple code.  I use them a great deal.

---

### Post by mc4man on 2009-04-16
If you wish to revisit rubyripper at some point here are a few links
Prebuilt .debs (hardy and intrepid

[http://www.getdeb.net/search.php?search_distro_id=11&keywords=rubyripper](http://www.getdeb.net/search.php?search_distro_id=11&keywords=rubyripper)

Slightly old but informative info

[http://filesharefreak.com/tutorials/rubyripper-native-secure-cd-ripping-on-linux/](http://filesharefreak.com/tutorials/rubyripper-native-secure-cd-ripping-on-linux/)

---

### Post by Pipps on 2009-04-16
K3b did the job nicely for me. I was also delighted to find that it had the functionality for a cue file too. Great stuff! :D

---

### Post by andrew.46 on 2009-04-16
Hi SuperSonic4,

> **SuperSonic4 said:**
> 
```
sudo cdparanoia -d /dev/sr1 -v 1-11
``` 


A small nitpick: it is better to quote the tracks "1-11" as the shell can misinterpret the '-' mark as an option.

> unless of course using cdparanoia is superfluous to your needs, k3b is rather easier XD

Mind you I believe that k3b actually uses cdparanoia, cdrdao and cdrtools for ripping and burning :-).

Andrew

---

