---
title: "Open source radeon driver VS fglrx??"
date: 2007-03-27
forum: Multimedia &amp; Video
---

### Post by WalmartSniperLX on 2007-03-27
What runs better? I just installed the fglrx driver on my other pc with a radeon 9250 and I think the open source driver ubuntu configured out of the box might have been better. However, I havn't begun tweaking it yet. Which is better?

---

### Post by diepruis on 2007-03-27
The open source driver is the better one if you're looking for stability and support. Also, if you want to use Beryl or Compiz, you must use one of the open source drivers (mesa / ati / radeon), since they're the only drivers that allow compositing for ATi cards.

If you are planning on playing games (i.e. if you want 3D acceleration), then you must use fglrx.

The situation is bad at the moment with ATi drivers, but the community is hopeful that they'll be getting their drivers up to standard in the near future.

---

### Post by matemargo on 2007-03-27
I have an ATI X700, and my situation with the drivers are the following:

opensource: beryl and 1027x768
fglrx: 1280x1024 and 3D acceleration.

**dieprui**: Do you have the same resolution problem with the open source drivers?

---

### Post by diepruis on 2007-03-27
> **matemargo said:**
> **dieprui**: Do you have the same resolution problem with the open source drivers?

I haven't tried them yet, since I don't want to break 3D acceleration, therefore my resolution is fine: 1280x1024. Have you tried tweaking your X.org conf file?

Just another thing: for some reason my X.org won't load with the ati driver. :shrugs:

I'll go check if I have any problems and let you know.

---

### Post by matemargo on 2007-03-27
> **diepruis said:**
> Have you tried tweaking your X.org conf file?
I have added the ModeLines, which only works with fglrx.

> **diepruis said:**
> 
Just another thing: for some reason my X.org won't load with the ati driver. :shrugs:

That's weird, maybe you should remove the fglrx drivers before.


Offtopic question: With the fglrx 3D acceleration, have you tried any good game?

---

### Post by diepruis on 2007-03-27
> **matemargo said:**
> I have added the ModeLines, which only works with fglrx.

Odd... my Mode lines work fine with 'radeon' and with fglrx.

> **matemargo said:**
> That's weird, maybe you should remove the fglrx drivers before.

This was before I even installed them :) Needless to say being dumped to a text interface on my first install was slightly unnerving.

> **matemargo said:**
> Offtopic question: With the fglrx 3D acceleration, have you tried any good game?

Oh yeah. UT2004, darwinia, defcon, etc. Go take a look at the gaming section of the forums, or check out this site: [http://www.linuxgames.com/](http://www.linuxgames.com/)

Mmm... well I tried the 'radeon' driver just now and it works fine, no resolution issues. Plus I now have compositing ;)

---

### Post by matemargo on 2007-03-27
May be it's my monitor, but it's odd because with fglrx driver works fine.

---

