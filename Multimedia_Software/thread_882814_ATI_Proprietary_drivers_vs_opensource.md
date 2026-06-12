---
title: "ATI: Proprietary drivers vs opensource"
date: 2008-08-07
forum: Multimedia Software
---

### Post by syms on 2008-08-07
Hello,
im trying to get my radeon 9600 propiertary drivers working, but now im wondering - why i should make them work if compiz is working almost nice with open source ati drivers. the only lag i see that window opening animation lags when that window must be maximised, and maximise wobble animation lags a bit. so the question is if ill get my poprietary ati drivers working, does ill have much better performance of compiz or beryl? and how much poprietary drivers are faster than open source? i dont play games at all, exept my good old doom (ill never get bored of it :) ) which runs on pentium 1 :D.
thanks for help.

---

### Post by tuxxy on 2008-08-07
I didnt think my compiz effects were bad at all until I upgraded to nvidia, try 3D aswell that was a problem for my ATI card/driver.

---

### Post by matt.taylor on 2008-08-07
I have never had a problem with the open source ati stuff, i have had problems with trying to install the ATI stuff though :oops:

---

### Post by Melcar on 2008-08-07
The open source driver is around 50-60% slower (and in certain situations even slower still) than the proprietary one and can only do up to openGL1.3.  Still, I prefer to use the open source one whenever I can since it's much more stable, has better video playback, and little to no flickering with accelerated videos while using composition managers (with gstreamer).  Provided you have a "fast" card, Compiz will run with no problems and you will still be able to play most games (except with Wine).
Check out these benchies I ran.  The initial purpose was to compare it to fglrx, but the driver wouldn't install :rolleyes:.  It's a 9800pro 128MB:

[http://global.phoronix-test-suite.com/index.php?k=profile&u=melcar-15688-6697-1621]("http://global.phoronix-test-suite.com/index.php?k=profile&u=melcar-15688-6697-1621")

---

### Post by ajgreeny on 2008-08-07
I think it depends entirely on your specific graphic card.  You have one of the better supported cards the 9600, and I'm lucky enough to have a 9200SE agp card which is well served by the OS driver.

Like Mat Taylor, I have not been able to install the proprietary drivers for this card since about version 5.04 or 5.10, and I've tried many times but always end up with a "no go" situation, but as it works fine for my requirements I don't bother about it any more and just use the OS version.

---

### Post by syms on 2008-08-07
thanks for help. that propertary driver is 50% faster is a good thing, but man, ive tried everythink! i followed many guids, used envy, restricted manager, edited many things but still i cant get running fglrx driver. so i have no other choice, i must use open source driver which is working very nice. but hey, does they will improve their open source drivers in intrepid ibex or later releases?

---

### Post by Melcar on 2008-08-07
> **syms said:**
> thanks for help. that propertary driver is 50% faster is a good thing, but man, ive tried everythink! i followed many guids, used envy, restricted manager, edited many things but still i cant get running fglrx driver. so i have no other choice, i must use open source driver which is working very nice. but hey, does they will improve their open source drivers in intrepid ibex or later releases?

I can't install the driver on any of my AGP cards either.  Installs fine on my PCI-e cards and IGPs however.  
As for the newer driver builds, I think that for that particular range of cards the only real improvement is EXA (better 2D acceleration basically).

More benchmarks comparing the drivers:

[http://global.phoronix-test-suite.com/index.php?k=profile&u=melcar-16732-14360-5380]("http://global.phoronix-test-suite.com/index.php?k=profile&u=melcar-16732-14360-5380")
[http://global.phoronix-test-suite.com/index.php?k=profile&u=melcar-31921-23141-15376]("http://global.phoronix-test-suite.com/index.php?k=profile&u=melcar-31921-23141-15376")
[http://global.phoronix-test-suite.com/index.php?k=profile&u=melcar-28501-16933-14679]("http://global.phoronix-test-suite.com/index.php?k=profile&u=melcar-28501-16933-14679")

---

### Post by jrasmussen0 on 2008-08-07
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

