---
title: "Will Dapper be &quot;multimedia ready&quot;?"
date: 2006-04-25
forum: Multimedia &amp; Video
---

### Post by Bristen Bourque on 2006-04-25
As per the comments on the main Ubuntu Studio Wiki page: << STATUS: Without the realtime-preemption patches from Ingo Molnar, Ubuntu is almost useless for true, very low-latency audio work. This is unfortunate, but if you want to use Ubuntu as a Studio, you have come to the right place! You will have to get your hands slightly dirty, and possibly face breaking some features, but it is well worth it. We have been in contact with Canonical, and they are working toward having a "Multimedia Ubuntu" ready at Dapper+1 release time. We hope to have some kind of input to this derivative, so if you would like to contribute, please get in contact with us. >>

Just wondering if I want to setup an Ubuntu Studio, should I wait for the final Dapper to come out?

Thanks,
  Bristen.

---

### Post by Belathor on 2006-04-25
I think this means Ubuntu studio won't be implemented until Edgy Eft comes out in October.

---

### Post by bwanab on 2006-04-25
[QUOTE=Belathor]I think this means Ubuntu studio won't be implemented until Edgy Eft comes out in October.[/QUOTE]

I don't think that's what it means. I'm pretty sure that Dana intends on building an audio ready kernel after the release of dapper. He's holding off since the kernel builds are still coming at a rate of one every week or two.

---

### Post by ubuntu27 on 2006-04-25
[QUOTE=Bristen Bourque]As per the comments on the main Ubuntu Studio Wiki page: << STATUS: Without the realtime-preemption patches from Ingo Molnar, Ubuntu is almost useless for true, very low-latency audio work. This is unfortunate, but if you want to use Ubuntu as a Studio, you have come to the right place! You will have to get your hands slightly dirty, and possibly face breaking some features, but it is well worth it. We have been in contact with Canonical, and they are working toward having a "Multimedia Ubuntu" ready at Dapper+1 release time. We hope to have some kind of input to this derivative, so if you would like to contribute, please get in contact with us. >>

Just wondering if I want to setup an Ubuntu Studio, should I wait for the final Dapper to come out?

Thanks,
  Bristen.[/QUOTE]

From what you are quoting http://ubuntustudio.com/wiki/index.php/Welcome,_Musicians!:

We have been in contact with Canonical, and they are working toward having a "Multimedia Ubuntu" **ready at Dapper+1 release time. **We hope to have some kind of input to this derivative, so if you would like to contribute, please get in contact with us.


That Dapper + 1 meas the next version after Dapper Drake.

Mark has decided to call Dapper + 1 "Edgy Eft" You can read it here: [http://www.ubuntuforums.org/showthread.php?t=162807](http://www.ubuntuforums.org/showthread.php?t=162807)

People are already discussing about Edgy Eft when Dapper is still nto realeased :D 

[http://www.ubuntuforums.org/showthread.php?t=162552](http://www.ubuntuforums.org/showthread.php?t=162552)

---

### Post by dolson on 2006-04-27
Ah, I forgot to update it when Mark sent the email about the next release's name. I updated that section a tiny bit.

Dapper will be much better than Breezy, but still will be lacking a realtime kernel. We will be working on that though, and if it can be done, we will indeed do it, and provide both a tutorial with a patch, and package downloads/repository.

---

### Post by Bristen Bourque on 2006-04-27
[QUOTE=ubuntu27][...] That Dapper + 1 meas the next version after Dapper Drake.
Mark has decided to call Dapper + 1 "Edgy Eft" You can read it here: [http://www.ubuntuforums.org/showthread.php?t=162807](http://www.ubuntuforums.org/showthread.php?t=162807)
People are already discussing about Edgy Eft when Dapper is still nto realeased :D 
[http://www.ubuntuforums.org/showthread.php?t=162552](http://www.ubuntuforums.org/showthread.php?t=162552)[/QUOTE]

ah ha!! Thanks for the explanation... I noticed the "+" thing, but didn't figure it out.. I thought it was something like the "released" version of Dapper or something... so we'll have to wait for Edgy Eft.. heh, that's a drag :(  Another 6 months, right?

Thanks for the info,
  Bristen.

---

### Post by ubuntu27 on 2006-04-27
[QUOTE=Bristen Bourque]ah ha!! Thanks for the explanation... I noticed the "+" thing, but didn't figure it out.. I thought it was something like the "released" version of Dapper or something... so we'll have to wait for Edgy Eft.. heh, that's a drag :(  Another 6 months, right?

Thanks for the info,
  Bristen.[/QUOTE]

Yep You're welcome. If you want to know more about Ubuntu read the [FAQ](http://www.ubuntu.com/support/faq) :)

Anyway, from the FAQ:

**Release information**
_What is the numbering system of the releases about?_

The version number comes from the year and month of the release, it really is that simple.

    *

      The first release (Warty Warthog) was released in October 2004, release number 4.10.
    *

      The second release (Hoary Hedgehog) was released in April 2005, release number 5.04.
    *

      The third release (Breezy Badger) was released in October 2005, release number 5.10.
    *

      The fourth release (Dapper Drake), release number 6.06, is scheduled for June 2006.

Each Ubuntu release has a unique combination of component versions - the Linux kernel, Xfree has been replaced with Xorg, Gnome, GCC, libc... so an aggregate version number does not make much sense. We prefer to show when the release took place.

If you see a name such as current development_name +1 what is being referenced is the version after the current development name, and the reason for the +1 is that the version after next has not got a name yet.


NB: You should never run software that is in development if you can't afford to loose all the data on the machine, although this is unlikely, it could happen. Yet another good reason for backups. :)

---

### Post by Rinzwind on 2006-04-27
Hmmm what's a 'real-time kernel'? 
Never saw that before :D

---

### Post by dolson on 2006-04-27
It's a kernel with the -rt patch by Ingo Molnar (of Red Hat) applied to it.

It improves pre-emption of the kernel from about 50% to 99%, and with it applied and your apps requesting (and receiving) RT access (via PAM, set_rlimits, running as root, or realtime_lsm), they are nearly uninterruptible. Meaning that I can, in GNOME, compile a kernel, run three copies of burnk7, chat on Gaim, surf with Firefox, check email in Evolution, all while playing music through XMMS with the JACK output plugin, patched into JACK-Rack to apply some effects. With 0 XRUNS.

Also, are you a Pratchett fan at all? :D

---

### Post by ubuntu27 on 2006-04-28
[QUOTE=dolson]It's a kernel with the -rt patch by Ingo Molnar (of Red Hat) applied to it.

It improves pre-emption of the kernel from about 50% to 99%, and with it applied and your apps requesting (and receiving) RT access (via PAM, set_rlimits, running as root, or realtime_lsm), they are nearly uninterruptible. Meaning that I can, in GNOME, compile a kernel, run three copies of burnk7, chat on Gaim, surf with Firefox, check email in Evolution, all while playing music through XMMS with the JACK output plugin, patched into JACK-Rack to apply some effects. With 0 XRUNS.

Also, are you a Pratchett fan at all? :D[/QUOTE]

Cool!

---

