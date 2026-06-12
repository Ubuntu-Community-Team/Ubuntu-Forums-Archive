---
title: "help installing the Restricted drivers fglrx with Radeon 9550"
date: 2009-11-27
forum: Multimedia Software
---

### Post by maxxerific on 2009-11-27
Hey all 
   i'm having a very hard time trying to get a decent performance out of my radeon 9550. 
At the moment it performs no better than my (32M) Viper. :) 

desktop effects can't be enabled etc etc

i tried installing the restricted drivers bu after using synatptic to install the 9.10 ver of catalyst, still nothing shows up under 'hardware drivers'

(also, maybe unrelated but my xorg.conf seems to have dissapeared)

sooooo what's the next step?

---

### Post by byStanderone on 2009-11-27
...i think that's the prob with proprietary, such as nvidia and ati. am on nvidia, my desktop effects won't work as well.

i'd assume you got the correct fglrx package for your machine.

---

### Post by Yellow Pasque on 2009-11-28
Your card is not supported by the restricted drivers anymore. Make sure you purge all of that stuff out: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

If you still have problems, then post/pastebin your /var/log/Xorg.0.log

---

### Post by maxxerific on 2009-12-04
okay - so i completely purged my system. 
   back to open source drivers.
  seems okay (although performance is pretty weak!) 
  
forgive my lack of understanding: isn't there an 'older' version of the restricted drivers that would work fine? Just because support has been abruptly dropped, doesn't mean i can't use what was working before.

ooooor, am i missing something (i.e. something in the way karmic handles graphics has broken the older versions of fglrx) Would i have to downgrade to 8.4 for example?

---

### Post by Yellow Pasque on 2009-12-04
> Would i have to downgrade to 8.4 for example?
Yes.

> Just because support has been abruptly dropped, doesn't mean i can't use what was working before. ooooor, am i missing something
The older drivers do not work on newer X servers.

---

