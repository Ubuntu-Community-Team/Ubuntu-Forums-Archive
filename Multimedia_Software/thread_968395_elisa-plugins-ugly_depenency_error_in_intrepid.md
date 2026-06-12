---
title: "elisa-plugins-ugly depenency error in intrepid?"
date: 2008-11-02
forum: Multimedia Software
---

### Post by s0l1dsnak3123 on 2008-11-02
Hi there, I am trying to install elisa-plugins-ugly, however, it tries to remove elisa-plugins-good, which also happens to be one of it's dependencies. I'm guessing this is a problem with the repo or the debs in question, or am i at fault? :KS

Thanks,
John.

---

### Post by katana2k on 2008-11-03
bump

---

### Post by Marshall2day on 2008-11-10
Same here, it doesn't play xvids at the moment and is basically useless for me now. I suppose the codec is included in the ugly package?

---

### Post by ciscophoneguy on 2008-11-11
I've tried installing elisa-plugins-ugly and it always errors out. Even when using apt-get. 

Right now, when launched it just goes to a black screen and I see nothing. I'll see the icons for a bit, maybe 2 seconds. After that the whole thing just goes black.

---

### Post by s0l1dsnak3123 on 2008-11-12
Has anybody fixed this error in the Repo yet? Elisa is quite a popular application. ](*,)

---

### Post by Rhubarb on 2008-11-12
Yeah, it's been annoying me too.
The only ways of getting it to work I guess would be to compile it yourself, or find an Ubuntu PPA repository that works.

I personally haven't checked, but there may be a Launchpad bug report on it.

---

### Post by regebro on 2008-11-25
Apparently, Fluendo hasn't created any 0.5 versions of that package, from what one bug report said. It might be deprecated. Don't know for sure.

---

### Post by lowi88 on 2008-12-12
Add the following line to /etc/apt/sources.list to get the latest elisa release:

deb [http://ppa.launchpad.net/elisa-developers/ubuntu](http://ppa.launchpad.net/elisa-developers/ubuntu) intrepid main

After that use synaptic to upgrade the elisa packages and install ugly plugins.

This worked for me.

---

### Post by tankerkevo on 2009-01-20
I've followed these instructions, however I still can't get the ugly plugins to install I'm runnning 64 bit. I wonder if that repo has been updated...including the ppa developer side...

---

