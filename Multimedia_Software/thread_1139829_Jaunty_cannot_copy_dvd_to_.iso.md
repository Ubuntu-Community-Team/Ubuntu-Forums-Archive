---
title: "Jaunty: cannot copy dvd to .iso"
date: 2009-04-27
forum: Multimedia Software
---

### Post by mealies on 2009-04-27
Hi Guys

I installed Jaunty x64 at the weekend and now am having a issue copying dvd to .iso image.  It was a Clean install(off USB thumb Drive). I used the comprehensive Multimedia & Video Howto guide on this forum to install the latest audio/video packages.

I have tried K9Copy (installed from Synaptic) as well as DVDFAB HD under wine (latest package from the wine site)

Both packages are unstable with frequent crashes.  When i can get either of them to copy the copy speed is around 0.3MB/S 

Any ideas on what can cause this? Also can anyone recommend a good DVD copy package?

Thanks 

Andrew

---

### Post by kpkeerthi on 2009-04-27
You can try vobcopy.
```
sudo apt-get install vobcopy
```

```
vobcopy -m
```
* -m option mirrors the whole dvd to harddisk. It will create a directory named after the dvd and copy the ifo, bup and vob files there.

---

### Post by mealies on 2009-04-27
Thanks very much 

It works a treat

Andrew

---

### Post by Sentience on 2009-05-27
I just tried this and it rips everything but the movie itself. It rips the intro screen, some other crap, everything but the part I care about, the film from credits to credits.

None of the other ones are working for me. K9 is unstable. Nothing I do is working.

---

### Post by Sentience on 2009-05-27
Nevermind. Now its ripping Pineapple Express just fine, but it wouldnt rip the Dark Knight....they must have some kind of encoding that beats it.

---

