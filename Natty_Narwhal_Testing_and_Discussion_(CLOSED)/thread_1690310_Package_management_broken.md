---
title: "Package management broken"
date: 2011-02-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by fallenshadow on 2011-02-18
This is the error I see when using update manager:

> 
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: parse error, in file '/var/lib/dpkg/available' near line 382 package 'python-aptdaemon':
 `Depends' field, invalid package name `python-so/lib/modules/2.6.38-3-generic/kernel/drivers/net/stmmac/stmmac.ko': character `/' not allowed (only letters, digits and characters `-+._')


Any ideas for a fix or do I need to wait until a packager fixes it?

---

### Post by nerdy_kid on 2011-02-18
try running 
```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by fallenshadow on 2011-02-19
I found a solution. I thought for some reason that this file got corrupted or something:

/var/lib/dpkg/available

So, I went to that location deleted the file "available" and renamed the file "available-old" to "available". I presumed that "available-old" was a backup of a working file.

It worked! :o I was then able to install all the updates but now Ubuntu won't bootup! LOL :p

---

### Post by nerdy_kid on 2011-02-20
> **fallenshadow said:**
> I found a solution. I thought for some reason that this file got corrupted or something:

/var/lib/dpkg/available

So, I went to that location deleted the file "available" and renamed the file "available-old" to "available". I presumed that "available-old" was a backup of a working file.

It worked! :o I was then able to install all the updates but now Ubuntu won't bootup! LOL :p

yeah....you usually want to make the backup yourself.  What error is Ubuntu giving you on boot?

---

### Post by fallenshadow on 2011-03-25
Bit late for a reply but I found out the bootup was being disrupted by Virtualbox additions and not Ubuntu itself.

I used failsafe X session and ran the uninstaller for virtualbox additions... problem solved! :)

---

