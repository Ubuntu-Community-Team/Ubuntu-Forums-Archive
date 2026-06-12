---
title: "Amarok 2 and last.fm scrobbing in Jaunty"
date: 2009-05-07
forum: Multimedia Software
---

### Post by huntz on 2009-05-07
**The problem:** Amarok 2 in Jaunty is not working scrobbing the music to last.fm service.

**The solution:** add to your sources list the kubuntu-experimental repository and update. The new version of Amarok 2 is working.

```

deb http://ppa.launchpad.net/kubuntu-experimental/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/kubuntu-experimental/ppa/ubuntu jaunty main

```

**My solution:** I don't like *experimental* packages into my *stable system*, so I have added the repository, updated only Amarok 2, then removed the kubuntu-experimental repository. In this way I have updated only Amarok 2 and some other dependencies, but not the whole KDE. Maybe into the future, Amarok 2 will be broken by some updates, but for now is working (fingers crossed! :) ).

Bye.

---

### Post by rainwalker on 2009-05-07
Honestly, I would recommend downgrading to Amarok 1.xx, because Amarok 2 is still so feature-lacking.

---

### Post by rmdegennaro on 2009-05-12
Worked for me, though one change to the repository list:
```

deb http://ppa.launchpad.net/kubuntu-experimental/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/kubuntu-experimental/ppa/ubuntu jaunty main
```
Also, Amarok sigv'ed after first start, but has been running  and scrobbling okay since. :guitar:

---

### Post by trybik on 2009-06-12
Update regardin repositories:

```

deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main

```

Note: adding key to keyring is not necessary.

---

### Post by uhoh_zombies on 2009-10-24
I've added the experimental repositories to my source list, and after reloading/updating I get this in both an error box in package manager and in terminal:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60487016493B3065
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2836CB0A8AC93F7A
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 39456311108B243F
W: You may want to run apt-get update to correct these problems

Please tell me there's a solution.

---

### Post by trybik on 2009-10-24
Add the repositories keys to the keyring
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 60487016493B3065
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2836CB0A8AC93F7A
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 39456311108B243F

```
(... it shouldn't be necessary though)

---

### Post by SuperSonic4 on 2009-10-24
> **rainwalker said:**
> Honestly, I would recommend downgrading to Amarok 1.xx, because Amarok 2 is still so feature-lacking.

Which features are these? Remember that just because *Ubuntu's* version of amarok is out of date that does not mean amarok is out of date

---

