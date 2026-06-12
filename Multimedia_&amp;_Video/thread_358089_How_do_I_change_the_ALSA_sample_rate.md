---
title: "How do I change the ALSA sample rate?"
date: 2007-02-10
forum: Multimedia &amp; Video
---

### Post by mjpatey on 2007-02-10
Hi, group-

I'm running the pre-release of Feisty, but I imagine this is the same in any release...

I just installed Ardour, and absolutely love it.  It runs as a client of Jack, which is set to use ALSA as its engine.

My problem is that the only way to change the sample rate is to tell ALSA to do so... but I don't know how.  There is no place in Ubuntu's Sound control panel to change from 44.1 to 48, and I just don't know where else to look.

Any ideas?

Thanks for any help you may have!

-Mark

---

### Post by sgx on 2007-02-10
> **mjpatey said:**
> Hi, group-

I'm running the pre-release of Feisty, but I imagine this is the same in any release...

I just installed Ardour, and absolutely love it.  It runs as a client of Jack, which is set to use ALSA as its engine.

My problem is that the only way to change the sample rate is to tell ALSA to do so... but I don't know how.  There is no place in Ubuntu's Sound control panel to change from 44.1 to 48, and I just don't know where else to look.

Any ideas?

Thanks for any help you may have!

-Mark
Start jackd like this...
jackd -d alsa -r 48000

insert rate of choice as desired, and if you wish to start jackd from qjackctl in the future,
apply the change there also, in the config panel, save, and restart qjackctl to verify the change stuck...

[http://lalists.stanford.edu/lau/2007/01/0397.html](http://lalists.stanford.edu/lau/2007/01/0397.html)

go to this link, and bookmark it, and as desired, change the month and year, so you can peruse years
of this linux audio lists' posts and discussions, always find some nuggets and jewels of info there, and
by all means, join the list and contribute/ask in the future! Have a great weekend...

remember, the same user must start all audio apps, no mixing su, root, or normal user...

---

### Post by mjpatey on 2007-02-10
Beautiful!  I knew it would be something simple like this.

Thanks for the resource, too!

-Mark

---

