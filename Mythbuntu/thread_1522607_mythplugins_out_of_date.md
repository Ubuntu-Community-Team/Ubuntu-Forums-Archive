---
title: "mythplugins out of date"
date: 2010-07-02
forum: Mythbuntu
---

### Post by mdaitc on 2010-07-02
Hi,

after a recent apt-get update/upgrade against the PPA i'm seeing:

2010-07-02 09:01:56.974 Plugin mytharchive (0.23.20100628-2) binary version does not match libraries (0.23.20100630-3)
2010-07-02 09:01:56.974 Test Popup Version Failed
2010-07-02 09:01:56.975 Unable to initialize plugin 'mytharchive'.
2010-07-02 09:01:56.980 Plugin mythgallery (0.23.20100628-2) binary version does not match libraries (0.23.20100630-3)
2010-07-02 09:01:56.980 Unable to initialize plugin 'mythgallery'.
2010-07-02 09:01:57.014 Plugin mythmusic (0.23.20100628-2) binary version does not match libraries (0.23.20100630-3)
2010-07-02 09:01:57.014 Unable to initialize plugin 'mythmusic'.
2010-07-02 09:01:57.020 Plugin mythvideo (0.23.20100628-2) binary version does not match libraries (0.23.20100630-3)
2010-07-02 09:01:57.020 Unable to initialize plugin 'mythvideo'.

mythvideo                             0.24.0~trunk25198-0ubuntu0~mythbuntu1
comapred to
libmyth-0.23-0                        0.24.0~trunk25247-0ubuntu0~mythbuntu1 

just wondering how to fix?

thanks!

---

### Post by brianafischer on 2010-07-02
Try another update.  I have had this issue before. I am assuming that you probably were downloading while the packages were being updated.

---

### Post by tgm4883 on 2010-07-02
Looks like the packages are still in the queue for building

---

### Post by mdaitc on 2010-07-02
> **tgm4883 said:**
> Looks like the packages are still in the queue for building

that's what i figured - just wasn't sure if 17+ hours is a typical build time, or if the queue gets stuck occasionally

i don't actually see the mythplugins in the list of stuff pending to build though: [https://launchpad.net/~mythbuntu/+archive/0.24/+builds?build_state=pending](https://launchpad.net/~mythbuntu/+archive/0.24/+builds?build_state=pending)

thanks,

---

### Post by tgm4883 on 2010-07-02
> **mdaitc said:**
> that's what i figured - just wasn't sure if 17+ hours is a typical build time, or if the queue gets stuck occasionally

i don't actually see the mythplugins in the list of stuff pending to build though: [https://launchpad.net/~mythbuntu/+archive/0.24/+builds?build_state=pending](https://launchpad.net/~mythbuntu/+archive/0.24/+builds?build_state=pending)

thanks,

Whoa you are right, I see where it is broke. I'll have to fix that when I get home tonight

---

### Post by mdaitc on 2010-07-02
cool, thanks!

it looks like the mythplugins has gotten out of sync with the mythtv - this i think is causing my version dependency issue - i'll wait till things settle down with the builds and see if they get resolved.

thanks,

---

### Post by tgm4883 on 2010-07-03
Yep there was a packaging bug that cropped up. It should be fixed in tonights builds. I've pinged the builder to see if we can push one early.

---

