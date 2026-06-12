---
title: "After update no more X.  Ati/fglrx."
date: 2008-06-24
forum: Multimedia Software
---

### Post by Aquaman420 on 2008-06-24
So I updated my 8.04 normally the other day via apt-get, then I went and did a reboot, I no longer could see anything.  After trying everything I knew, which isn't extensive, I reluctantly reinstalled and now I can no longer install fglrx without problems let alone even change my resolutions without having to do the old dpkg-reconfigure.... command.  What gives?  I am going crazy.  I have tried numerous tuts, numerous times with no luck, does the new kernel not like fglrx anymore? I even tried to use the open drivers,radeon, but they too didn't work. Any help is appreciated because I no longer have the time to mess around with random breakages like I once did...Family man and all that now and I need a working computer for my sanity!!

---

### Post by pytheas22 on 2008-06-24
I don't know if it's going to solve the problem, but if you haven't done so already, it could help to try envy.  To install:
```

sudo apt-get install envyng envyng-gtk
```

and to run:
```

sudo envyng-gtk
```

tell it to download the right driver and configure your machine automatically.  I've seen envy do in three minutes what a roomful of people with 20+ years of collective Linux experience couldn't do in two hours, so it's worth a try.

---

### Post by Aquaman420 on 2008-06-25
Thanks for the response pytheas22 but I have already tried envy.  I think I have a couple problems the biggest being the resolution change, the drivers could have totally worked but I can't see them because the resolutions are wrong.  Well back to the drawing board when I get some free time.

---

### Post by markbuntu on 2008-06-25
There is an ongoing thread around here about the Radeon 1650 card. It seems to have some peculiar problems all of its own. Try a search for that.

---

