---
title: "ALSA Stops Working"
date: 2008-08-17
forum: Multimedia Software
---

### Post by bm90 on 2008-08-17
I'm pretty new to Ubuntu, but I've been having a bit of trouble with ALSA.

When I first installed Ubuntu, it worked perfectly, but then I lost sound all the sudden. 
Going to System > Preferences > Sound, I tested the sound playback, and there was no sound on any of the choices (Autodetect, Intel ICH6 - IEC958, Intel ICH6, CA0106, CA0106, CA0106, CA0106, ALSA, OSA, Pulse Audio Sound Server) apart from the forth "CA0106"

So, to try and get ALSA working again, I reinstalled it following the instructions in this thread.
[http://ubuntuforums.org/showthread.php?t=820959&highlight=alsa](http://ubuntuforums.org/showthread.php?t=820959&highlight=alsa)

It worked fine for 2 days, but today ALSA stopped again. I've restarted it with the command 
```
sudo /etc/init.d/alsa-utils restart
```
But nothing.

This is my sound card details (I think)
> id:	
multimedia
description: 	Multimedia audio controller
product: 	SB Audigy LS
vendor: 	Creative Labs

I think that something maybe overwriting files that ALSA uses, but I don't know how to check.
I'd appreciate any help you could offer me as to why this is happening, and how to stop it.

Thanks :)

---

### Post by bm90 on 2008-08-18
The problem seems to be fixed now after reinstalling some alsa components.


```

apt-get remove alsa-base --purge

apt-get remove alsa-oss --purge

apt-get install alsa-base

apt-get install alsa-oss

```

---

### Post by bm90 on 2008-08-20
I've re-marked the thread as unsolved, as it has stopped working again, and those commands above no do nothing now.

I haven't installed any updates since then, but its just stopped again?

Help please.

Edit: It works again after reconfiguring it
```
sudo dpkg-reconfigure alsa-base
sudo dpkg-reconfigure alsa-utils
```

I'm not sure whether to mark it solved again, as it will probably break in a few days time again.

---

