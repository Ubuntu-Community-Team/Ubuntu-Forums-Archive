---
title: "alsa-utils not found ?"
date: 2011-08-09
forum: Multimedia Software
---

### Post by redn123ax on 2011-08-09
Hello,

I installed ubuntu today and noticed that the sound isnt right..
It sounds like you hear music with you hand on your ears..

So i looked on the internet and found this:
[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

The first thing it makes me do is stop the alsa-utils deamon
BUT....
I dont have alsa-utils....

when i go to /etc/init.d/ i only see alsa-store & alsa-restore.
nothing else..

what should i do ?
(this is on the MSI GX740 laptop)

thanks in advance
ReDNaX

---

### Post by dniMretsaM on 2011-08-09
Install them maybe? I would think it would be
```
sudo apt-get install alsa-utils
```
Although I don't know how much good that would do you if you're just going to stop it.

---

### Post by redn123ax on 2011-08-09
That gives a message that i already have the latest version..
and i think they just removed it from Ubuntu 11.04

but i use it for more then just stop it.. i can't execute other commands without alsa-utils

---

### Post by dniMretsaM on 2011-08-09
Strange. I don't know then. Cue somebody experienced.

---

### Post by .... on 2011-08-09
Ubuntu 11.04 already has the latest alsa (1.0.24) software utilities. The only thing that might help to upgrade is the kernel module (see ubuntu audio dev ppa).

---

### Post by redn123ax on 2011-08-12
Ok i got it fixed..
I tried your stuff, but that didn't help unfortunately :(

But after more research i found this site: [http://www.backtrack-linux.org/forums/backtrack-5-beginners-section/41508-alsa-problem-after-successful-update.html](http://www.backtrack-linux.org/forums/backtrack-5-beginners-section/41508-alsa-problem-after-successful-update.html)
It said i should add this line "options snd-hda-intel index=0 model=acer-aspire-7730g" to the options in /etc/modprobe.d/alsa-base.conf

so i did that and restarted my laptop.. and didn't have any problems at all :D

Thanks for all of your help guys :D

---

