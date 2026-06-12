---
title: "VLC won't play DVDs anymore (after upgrade)"
date: 2006-12-10
forum: Multimedia &amp; Video
---

### Post by Robert Leithe on 2006-12-10
Hi,

My VLC Player has been upgraded to 0.8.6, and since I rebooted my computer it won't play DVDs anymore. Had a DVD in my PC, watching it prior to the reboot. After the reboot, the same DVD won't play anymore.

Seems as if I had this same problem when I first installed 6.10 (something about DVD codecs???), but I cannot seem to find the answere - although not for lack of trying.
I start VLC, press Play, select the DVD-tab and click OK. But the disc won't play. 

When I try to play the same disc with Movie Player I receive this message:

An error occured
The source seems encrypted, and can't be read. Are you
trying to play an encrypted DVD without libdvdcss?

I checked my Synaptic Package Manager, and libdvdcss2 is installed (along with libdvdread3).
I also ran Automatix2 and un- then reinstalled "AUD-DVD Codecs".

So I'm trying the easy way out - HELP! ;)

Can someone help me back on track here?

Sincerely

EDIT: Well, after a couple of reboots, VLC now play DVDs again :-/

---

### Post by Ryan Swanson on 2008-02-23
Hi Robert,

I had a similar problem.  After searching for what seemed like forever, I found this webpage.  

[http://limulus.wordpress.com/2007/12/10/playing-dvds-in-ubuntu-gutsy/](http://limulus.wordpress.com/2007/12/10/playing-dvds-in-ubuntu-gutsy/)

It gives a step-by-step guide to installing and setting up VLC properly.  I used it and now my DVD's mount and play automatically.

Coincidentally, the medibuntu software repository you are asked to add as a source has some other cool software.  (BONUS!!).  I should also not that  when you add the repository and you get a error telling you that you need a key, don't be discouraged.  Just use the Synaptic Package Manager to download "gui-apt-key" like the article says, input the key the article gives, and everything will be peachy.

Best Regards,
Ryan

---

