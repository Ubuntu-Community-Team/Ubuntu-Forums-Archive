---
title: "Ripping a DVD To My HDD?"
date: 2006-12-01
forum: Multimedia &amp; Video
---

### Post by CarlosinFL on 2006-12-01
I purchased a new CD and it came with a DVD bonus of concert footage and what not. Can someone please explain how I can take the DVD contents and rip it to my local drive as a .MPEG so I can watch this and any media player / OS?

Thanks for any help as I am really trying to understand this process.

---

### Post by Shatrat on 2006-12-01
There is a program called dvd rip which should be able to do this, although I haven't tried it with DvD content on audio cds before.  You can install it through automatix or I'm sure you can find some other repository if you search.

---

### Post by CarlosinFL on 2006-12-01
I can't seem to find dvd-rip or automatix2 in my repo. Can someone please tell me how I can install automatix?

Their website has been down for sometime...

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by Shatrat on 2006-12-01
[http://www.exit1.org/dvdrip/](http://www.exit1.org/dvdrip/)
There is the site for DVD::Rip which can be installed through Automatix.  They don't seem to have their own ubuntu repository but they do have various debian ones.  I dont know how compatible different repositories are.

I can see dvdrip in synaptic, although I don't know if it was already in one of the standard repositories or if it is coming from one of the repositories installed by Automatix.

Here are the repositories that Automatix added to my /etc/apt/sources.list
```
#AUTOMATIX REPOS START

#deb http://wine.lowvoice.nl/apt dapper main

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe mul
tiverse

deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multi
verse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe mult
iverse

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
#AUTOMATIX REPOS END


```

---

