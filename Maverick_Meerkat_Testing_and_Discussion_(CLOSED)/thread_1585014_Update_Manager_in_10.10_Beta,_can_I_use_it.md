---
title: "Update Manager in 10.10 Beta, can I use it?"
date: 2010-09-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by brotheralwyn on 2010-09-29
It's been a while since I've used Ubuntu, but I wanted to check out the 10.10 Beta release. I did a clean install which worked great. I then went to "Update Manager" to see if there was any updates since the Beta ISO was made.

It comes up saying "Not all updates can be installed. Run a partial upgrade, to install as many updates as possible". It also shows 483 updates selected. Are you not supposed to run the update manager on Beta releases? Will I be able to "upgrade" to the final release? How do I get updates?

Thanks!

---

### Post by drs305 on 2010-09-29
I've moved your thread to Maverick Testing, since it is still in beta.

But to your question, please read the 'sticky' in this forum:
[Update Manager Offers a "Partial Upgrade"? Read This.]("http://ubuntuforums.org/showthread.php?t=1479146")

I think it will answer your questions.

---

### Post by ktp on 2010-09-29
Please see following thread on partial upgrade:

[http://ubuntuforums.org/showthread.php?t=1479146](http://ubuntuforums.org/showthread.php?t=1479146)

You can also try doing safe-upgrade via console:
> sudo aptitude safe-upgrade

---

### Post by 23dornot23d on 2010-09-30
I second that .... partial uprades seem to bork peoples systems up ....

sudo apt-get install aptitude
sudo aptitude update
sudo aptitude safe-upgrade

has worked for me at least all the way through development with no major issues ...

---

### Post by 23meg on 2010-09-30
[QUOTE=brotheralwyn]Are you not supposed to run the update manager on Beta releases?[/QUOTE]

No, you can run it. Just be careful what it wants to remove (same goes for all package management tools), and evaluate the partial upgrade offers carefully (details in the thread linked to above).

[QUOTE=brotheralwyn]Will I be able to "upgrade" to the final release?[/QUOTE]

Yes, but under certain circumstances you may not want to. You'll see that clarified in [another sticky thread]("http://ubuntuforums.org/showthread.php?t=1500648") in this forum.

---

### Post by KegHead on 2010-09-30
Hi!

Updated today via terminal w/no issues.

KegHead

---

