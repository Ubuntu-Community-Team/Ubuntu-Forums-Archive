---
title: "For the guitarists"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by Nonno Bassotto on 2006-06-08
If there is a guitarist who is also accustomed with building deb packages, he may want to try out kTabEdit
[http://kguitartmp.sourceforge.net/](http://kguitartmp.sourceforge.net/)
which is a fork of kGuitar with intial support to PowerTab files.
I tried to build it on my own, I had to install a lot of dev packages to do this (I never had compiled anything before), but then I wasn't able to finish the task. This is because one of these dev packages had a dependency on some repos fonts package, while I have installed patched fonts packages, so synaptic wasn't able to solve the dependencies. I think it should not be too difficult if one already has dev packages installed (quite standard ones, I think, mainly X and Qt related).
If one succeed and obtains a working deb, please consider making it available (for example I think that the original author may be happy to publish the built package on his site).
Thank you

---

### Post by matthew on 2006-06-08
I'll let someone else look into creating a .deb if they want to. The program you are referring to looks quite nice and would be an asset.

In the meanwhile, kguitar, which you referred to, is in the repositories--although I know it doesn't have the functionality you are looking for.

You might consider gnometab, which is also in the repos, for creating tab. I'm not sure if it specifically uses the PowerTab format, but it might be worth a look.

EDIT: I also found songwrite in the repos for making tabs.

---

### Post by Nonno Bassotto on 2006-06-08
Actually I don't have to create tabs. I only have to open tabs made by other people in ptb format, and i was looking for a way to do this natively in linux.

---

### Post by matthew on 2006-06-08
[quote=Nonno Bassotto]Actually I don't have to create tabs. I only have to open tabs made by other people in ptb format, and i was looking for a way to do this natively in linux.[/quote]I see. After some searching around it appears that the program that makes PowerTab files (ptb) is Windows only with no plans to change that. However, this looks like it may help you convert them to plain text (ASCII) files. You might want to look into it further.

[http://freshmeat.net/projects/ptabtools/](http://freshmeat.net/projects/ptabtools/)

---

### Post by EddieA on 2006-09-16
Doesn't TuxGuitar import Powertab 1.7 files?

---

### Post by Nonno Bassotto on 2006-09-16
> **EddieA said:**
> Doesn't TuxGuitar import Powertab 1.7 files?

Yes, and in fact now I'm not able to find information about KTabEdit anymore. But when I first posted I didn't know TuxGuitar existed, and I was not able to find anything which would open ptb files. Anyway I have to say I'm still using Powertab with wine rather than TuxGuitar, because the scores look much more polished.

---

