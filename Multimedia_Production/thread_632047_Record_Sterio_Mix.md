---
title: "Record Sterio Mix"
date: 2007-12-05
forum: Multimedia Production
---

### Post by MNICY on 2007-12-05
Anyone know a way to record the sounds directly that come out of the computer speakers?

You know, in windows you select "Sterio Mix" or "What U Hear" and then use the regular MS sound recorder....

I cant find a way to do it. I used the regular sound recorder, Audacity, searched the forum, etc....

no luck. 
Help would be appricated. 
Thanks in advance.
-MNICY

---

### Post by Stochastic on 2007-12-05
Well the simplest way to do this is to get a cord that runs from the soundcard out to the soundcard in, then hit record on sound recorder.  If this isn't feasable, or if you're terribly worried about the signal quality loss with that method, try using qjackctl.  It may not work for all your apps' sound output, but any apps that use jack can then be routed to any recording app (ardour, audacity, rezound, jokosher, etc...).  Is there a particular app you're trying to record?

---

