---
title: "How to install Ruby Ripper in Maverick?"
date: 2011-03-18
forum: Multimedia Software
---

### Post by gabriella on 2011-03-18
Hi,

I'm trying to install Rubyripper into Maverick using these guidelines:
[http://ubuntuforums.org/showthread.php?t=799621](http://ubuntuforums.org/showthread.php?t=799621)

But I get this error message in terminal:

```
W: Failed to fetch http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Presumably because it can't find the package. But what do I do next?
or is there an alternative way to install?

Thanks

---

### Post by shantiq on 2011-03-18
hi gabriella


Maybe forget the PPA and use a Lucid [getdeb]("http://linuxappfinder.com/package/rubyripper")
but i am told by people who know that getdeb can be a little weird although i have used this one and fine

your choice

---

### Post by cottfcfan on 2011-03-18
I just added the getdeb ppa to my sources from here:
[http://www.ubuntuupdates.org/ppas/25](http://www.ubuntuupdates.org/ppas/25)
Then installed rubyripper from synaptic.
Works a treat.

---

### Post by gabriella on 2011-03-18
> **shantiq said:**
> hi gabriella


my guess is and i cannot remember but you simply use an earlier version    edit in your software sources thus

change the word [COLOR="Red"]maverick[/COLOR] for [COLOR="Red"]lucid[/COLOR] in both sources

system/admin/software sources/other software/click on both places where aheck ppa are situated and edit

then start again   not sure he ever made one for maverick but it does not matter as the lucid one works


Thanks Shantiq. I changed Maverick to Lucid in the Software Sources and installed from Synaptiq!

> **cottfcfan said:**
> I just added the getdeb ppa to my sources from here:
[http://www.ubuntuupdates.org/ppas/25](http://www.ubuntuupdates.org/ppas/25)
Then installed rubyripper from synaptic.
Works a treat.

I tried this but it still didn't show up in Synaptic. Maybe I did something wrong. However, I left it in Software Sources as it's usefull to have. Thanks!

---

