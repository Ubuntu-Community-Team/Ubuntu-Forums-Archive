---
title: "Heads up: DVDFab HDDecrypter now working under wine"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by anjilslaire on 2007-10-27
After months of struggling with this app, I've now found that Kubuntu Gutsy 7.10 with wine 0.9.46  supports DVDFAB HDDecrypter 3.2.1.0. This is great news for dvd enthusiasts using linux, as there is a currently updated free app that works for us. See details here: [http://club.cdfreaks.com/f116/dvdfab-hddecrypter-linux-220283/ ]("http://club.cdfreaks.com/f116/dvdfab-hddecrypter-linux-220283/")

I've posted previously that part of DVDFAB is GPLed, and that the dev fengtao would release the sourcecode. Anybody up to playing with it to make a native client if possible?

---

### Post by disturbedite on 2007-10-27
i always used dvd decrypter, it seemed to work best to me.
but with wine 0.9.48 just released maybe it'll run even better?,,,

---

### Post by anjilslaire on 2007-10-27
DVD Decrypter works great, but the newer protections like Sony Arccos aren't bypassed by it, as development stopped quite some time ago.

However, the newer dvdfab decrypter can manage the newer protections, and now works under wine, so it's a good thng.

---

### Post by disturbed1 on 2007-10-28
> **anjilslaire said:**
> **_and now_** works under wine, so it's a good thng.


Did I miss something here? I've been using DVDFab with wine since the 0.9.3x releases (Fiesty). I always used DVD Decrypter before as well, until DVDFab matured enough to be usefull. I know it installed and ran in Dapper as well, but just didn't have the same features nor ability as DVD Decrypter at the time. DVD Decrypter + PGC Edit is still the most powerful toolset to use IMO.

---

### Post by anjilslaire on 2007-10-28
> **disturbed1 said:**
> Did I miss something here? I've been using DVDFab with wine since the 0.9.3x releases (Fiesty). I always used DVD Decrypter before as well, until DVDFab matured enough to be usefull. I know it installed and ran in Dapper as well, but just didn't have the same features nor ability as DVD Decrypter at the time. DVD Decrypter + PGC Edit is still the most powerful toolset to use IMO.

Yes, I've seen hit & miss reports of it working, but whenever I would try previously, the whole process would complete, but the output would be all green & pixelated, pretty much useless.

If I've been the only one missing out, oops. Sorry for the spamming.

---

### Post by disturbed1 on 2007-10-28
I've had that problem as well, but figured out what caused it ;)

If you access the drive with anything else besides DVDFab after inserting the disc, then you'll get this problem of the green and blocky rips.

I chalked it up to either libdvdcss and/or a wine xv problem.

---

### Post by anjilslaire on 2007-10-28
> **disturbed1 said:**
> I've had that problem as well, but figured out what caused it ;)

If you access the drive with anything else besides DVDFab after inserting the disc, then you'll get this problem of the green and blocky rips.

I chalked it up to either libdvdcss and/or a wine xv problem.

Really? wow, thats good to know! I'd been fighting with that for months. So, do you recommend inserting th disc, do whatever you want (if anything), THEN load up DVDFab?

Interesting...

---

### Post by disturbed1 on 2007-10-28
As long as nothing is allowed access to the disc before DVDFab. Don't let anything auto play the disc.

I install the latest wine deb from synaptic, then run winecfg in the terminal, set up my drives so it mounts my CDROM/DVDROM drives correctly, and set the OS to Win2000. The only program I've found that, that doesn't work well for is DVDDecrypter, which I override for that program only, using NT4.0.

---

### Post by wild77 on 2007-10-28
> If you access the drive with anything else besides DVDFab after inserting the disc, then you'll get this problem of the green and blocky rips.
I chalked it up to either libdvdcss and/or a wine xv problem.

I had the same problem  turn off autoplay and all should be ok, I have not installed libdvdcss yet so I do not think that is the problem.

---

