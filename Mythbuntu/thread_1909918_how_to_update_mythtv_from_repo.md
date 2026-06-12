---
title: "how to update mythtv from repo?"
date: 2012-01-16
forum: Mythbuntu
---

### Post by ubnewbie2 on 2012-01-16
On this page [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)  after installing the repos, it says

> Common use cases for using Mythbuntu Repos.
You want to stay up to date on a particular version of MythTV in order to get bug fixes.
Enable MythTV Updates and select the version of MythTV you want to keep up to date. 

I have no idea where I can do this.  Update manager just reports no updates available.    Did the repos install properly (how do I check)?

---

### Post by superm1 on 2012-01-16
You can double check graphically that they were installed right by going into mythbuntu control centre on the repos tab.

Or you can check by hand by looking at the files /etc/apt/sources.list.d/mythbuntu*

---

### Post by ubnewbie2 on 2012-01-16
> **superm1 said:**
> You can double check graphically that they were installed right by going into mythbuntu control centre on the repos tab.

Or you can check by hand by looking at the files /etc/apt/sources.list.d/mythbuntu*

I have

```
deb http://ppa.launchpad.net/mythbuntu/0.24/ubuntu oneiric main
deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu oneiric main
```

Is that right?  The 0.24 one seemed correct, but what about the 'testing' one?

Anyhow, I have some updates appearing now, so it is probably working.

Thanks.

---

### Post by superm1 on 2012-01-17
Looks correct to me.  That "testing" repo is used for pushing updates that don't come through the ubuntu chain for mythbuntu only tools like MCC or mythbuntu-bare.

---

