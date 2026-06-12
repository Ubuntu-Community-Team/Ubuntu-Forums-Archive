---
title: "am I running the beta or the release candidate?"
date: 2010-09-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by e1ektrob0y on 2010-09-30
I installed the maverick beta a week or so ago. If I simply run ```
apt-get update && apt-get upgrade
``` am I automatically running the release candidate? or do I have to download an ISO and do a fresh install?

edit: is there a way to find out which version I am running?

---

### Post by whoop on 2010-09-30
> **e1ektrob0y said:**
> I installed the maverick beta a week or so ago. If I simply run ```
apt-get update && apt-get upgrade
``` am I automatically running the release candidate? or do I have to download an ISO and do a fresh install?

edit: is there a way to find out which version I am running?

Yes everything will happen automatically, I advise you to run
```

sudo aptitude update && sudo aptitude safe-upgrade

```
instead of the update procedure you are using... It's safer.

---

### Post by e1ektrob0y on 2010-09-30
> **whoop said:**
> Yes everything will happen automatically, I advise you to run
```

sudo aptitude update && sudo aptitude safe-upgrade

```
instead of the update procedure you are using... It's safer.

Ok interesting. What does it do that is safer? Will I miss out on things if I do it that way?

---

### Post by 23meg on 2010-09-30
Barring last minute changes to the RC candidate images [that are subject to ISO testing right now]("http://ubuntuforums.org/showthread.php?t=1584009"), you're running the release candidate.

There's [a sticky thread]("http://ubuntuforums.org/showthread.php?t=1500648") clarifying this and similar issues that you might be interested in reading.

---

### Post by Funnnny on 2010-09-30
+1 for using safe-upgrade

---

### Post by 23meg on 2010-09-30
> **e1ektrob0y said:**
> Ok interesting. What does it do that is safer?

Practically nothing. "aptitude safe-upgrade" will install new packages to satisfy dependencies (you can override that with --no-new-installs), whereas "apt-get upgrade" will not. So strictly speaking, apt-get is actually "safer", but in practice, unless there's an inconsistency in the package archive and you're not reviewing the changes the package manager is suggesting, you'll be "safe" with both.

---

### Post by e1ektrob0y on 2010-09-30
awesome, thanks :)

---

