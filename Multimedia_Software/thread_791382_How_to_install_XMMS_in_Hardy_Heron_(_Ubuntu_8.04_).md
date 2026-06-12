---
title: "How to install XMMS in Hardy Heron ( Ubuntu 8.04 )"
date: 2008-05-12
forum: Multimedia Software
---

### Post by sistoviejo on 2008-05-12
I have noticed that even though xmms was removed from the repositories in Hardy Heron some packages still require it.
This is very annoying because it makes it impossible to install those packages.
Also XMMS 2 is no replacement to XMMS.
But don't worry! Here's a guide to install XMMS on Hardy:
[http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html](http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html)
Cheers!

---

### Post by bytor4232 on 2008-06-06
you could always do what I did.  Give up on xmms and move to audacious and switch to the refugee skin.  Looks identical to xmms.

---

### Post by antmenj on 2008-06-28
After installing audacious and haveing it crash on every track I did the above and XMMS is now playing perfectly on hardy.

Thanks to sartek.:guitar:

---

### Post by starcannon on 2008-06-28
Thanks man, its one of the oldest, and still the greatest in my book.
I have no idea why its been removed from the repo's its one of my few gripes with Hardy.

Better still, digging through the posts at the link you gave, we don't even have to compile it.
Heres the official hardy package that for some reason isn't in the repo's

[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

Binary ftw, thanks again man, wouldn't have found it without your detective work.

For those that keep saying "just use audacious", feel free, be my guest, its a nice program, I just happen to really like xmms, its nothing against any other software, I promise not to evangelize, do me the same courtesy.

---

### Post by markbuntu on 2008-06-28
Besides all that, streamtuner does not work with audacious or rythmbox and totem isn't really a good interface for streaming audio but streamtuner does work with xmms. Be sure and set the xmms output plugin to alsa so it can play nice with other apps.

---

### Post by fanders on 2008-06-29
Thank you, thank you and thank you.  I installed the old xmms as linked above along with streamtuner from the repos; works like a charm.  I like streamtuner a lot and was disappointed that I could not get it to work in Heron until I found this excellent thread.  

Regards,

Frank=D>

---

### Post by cozmicharlie on 2008-06-29
Add to the list of what makes xmms a great player - it is the only player that will handle shn files.  For those interested, there is a tutorial for adding the shn plugin for xmms here ([http://ubuntuforums.org/showthread.php?t=833164](http://ubuntuforums.org/showthread.php?t=833164)).

---

### Post by padeco on 2008-06-30
many thanks!
i followed the link / info above and installed xmms and it works great. also, i am now able to use streamtuner.

great stuff!
padeco

---

### Post by Leviathan88 on 2008-07-12
Thanks!  This was exactly what I was looking for.  :guitar:  Now I can finally use my streamtuner properly.

---

### Post by gandaran on 2008-07-12
> **markbuntu said:**
> Besides all that, streamtuner does not work with audacious or rythmbox and totem isn't really a good interface for streaming audio but streamtuner does work with xmms. Be sure and set the xmms output plugin to alsa so it can play nice with other apps.

streamtuner does work with audacious, rhythmbox or just any other player, all you have to do is change the player in preferences from xmms to the player of your choice.

---

### Post by Jimbotronics on 2008-07-12
> **gandaran said:**
> streamtuner does work with audacious, rhythmbox or just any other player, all you have to do is change the player in preferences from xmms to the player of your choice.

It is often said that Streamtuner works with all sorts of other audio players, but in my experience, I could only get it to work sporadically with Audacious (as a replacement for xmms) and NOTHING ELSE.  Recently, Audacious completely stopped working for me with Streamtuner, even after a reinstall.

I too gave up on everything else and installed XMMS from the Debian package, and life with Streamtuner is once again GREAT! :guitar:

---

### Post by roscal on 2008-09-04
I recently installed 8.04 on a fresh install, and was 
kinda dismayed about XMMS not being available anymore?

[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

That did the trick.
:)

Back in business.:guitar:

---

### Post by GnomviD on 2008-09-11
XMMS reigns supreme over all the other media players availible, and I've been hurting bad without it.

You are a golden god for this.

---

### Post by antmenj on 2008-11-11
I just did another install on another machine and this time rather than building it from source I installed XMMS useing the .deb from launchpad.  It works but I can't seem to work out how to link the equalizer and playlist to the main player so when the player is minimised the EQ and playlist go with it.

Any ideas on how to link them:confused:.

On passed installs you just push them together and they seem to lock to each other.
=============
Edit:
The new install from the .deb does all sorts of tricky looking flips etc when minimising but the install I built my self just goes down to the bottom bar same as it did on previous installs like dapper.

========================================
SOLVED
System ----> Preferences ----> Appearance ----> Visual affects ----> None

---

