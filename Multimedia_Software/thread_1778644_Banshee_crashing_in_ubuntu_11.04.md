---
title: "Banshee crashing in ubuntu 11.04"
date: 2011-06-09
forum: Multimedia Software
---

### Post by saabmnan on 2011-06-09
Hi :)
I have looked around a bit and found nothing yet so I am posting here:

I have an ACER Aspire One Netbook and have just installed ubuntu 11.04 on it to completely replace Window 7
All is going well except banshee player just freezes everything when I launch it...
Tried uninstalling-reinstalling twice but no change...

Has anyone experienced this kind of issue?

Thanx for any help you can offer ;)

---

### Post by Syd35 on 2011-06-10
I also have a freeze whenever I attempt to open Banshee. I have an Acer Aspire 5740 notebook with Ubuntu 11.04, installed in April. Everything worked nicely, even Banshee, until 2 days ago. I have tried several re-installations of Banshee, to no avail. I have now removed it.
I have seen some online reference to a file like ~/.config/banshee addins........, or something like that, related to a bug. Does anyone know if there is a bug, what and where the appropriate file is, and what should be the remedial action.
Help!!!!
Thanks

---

### Post by Syd35 on 2011-06-10
I appear to have fixed my problem with Banshee. At the link below, it was suggested to 'run' a debug on banshee in terminal mode; as **debug --banshee**. The next step suggested was to remove 3 .dll files. Well as soon as I did the debug as sudo, the problem disappeared and Banshee automatically loaded and is working OK. I never got as far as deleting the files.
Hope this helps someone else. 



[http://ubuntuforums.org/showthread.php?t=1554252&page=2](http://ubuntuforums.org/showthread.php?t=1554252&page=2)

---

### Post by Syd35 on 2011-06-11
I will retract my previous statement. Banshee still freezes my system. It worked at one stage after running 'debug'. Now it has failed again, and removing those three files had no effect.
Help

---

### Post by hybridxdawn on 2011-06-11
I get occasional freezes and crashes as well, but not consistently.

---

