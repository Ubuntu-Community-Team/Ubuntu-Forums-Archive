---
title: "Installing latest Flash (v24 beta)"
date: 2016-11-10
forum: Multimedia Software
---

### Post by adfh on 2016-11-10
Hi folks,

Did a search using google for hits in the past year on Flash before posting this, so if someone's answered it, please feel free to point me in that direction.

Adobe has started releasing newer versions of Adobe Flash Player for Linux. They don't have all the features of the other platforms, but they are more up-to-date security wise from reports that were published about the place, with both NPAPI and PPAPI variants provided.

[http://labs.adobe.com/downloads/flashplayer.html](http://labs.adobe.com/downloads/flashplayer.html)

Ubuntu offers multiple packages to pull in Flash, but they all seem to pull in the 11.2.202.644 version. My understanding is that the "adobe-flashplugin" method is the official method from the partner repository, but it, too, uses the older version.

```
$ apt-cache show flashplugin-installer | grep -i version
Version: 11.2.202.644ubuntu0.16.10.1
Version: 11.2.202.637ubuntu1
$ apt-cache show adobe-flashplugin | grep -i version
Version: 1:20160712.1-0ubuntu0.15.10.1
$ apt-cache show flashplugin-downloader | grep -i version
Version: 11.2.202.644ubuntu0.16.10.1
Version: 11.2.202.637ubuntu1
```

How have people cleanly tried the new version, or have you just been extracting the tarball manually?
I vaguely recall that one of the flash installer packages allows you to specify the tarball you want to install if you don't want it fetching what it thinks is the latest version. I think it's a bit of a shame that Adobe provide a tarball and an RPM, but not a DEB.

---

### Post by QIII on 2016-11-10
Hello!

Have a look [here]("http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html").

If you are running 16.04 or later you can just install from the repos.  However, if you want to get the latest versions as they come out, you can use the PPA.

Cheers!

---

### Post by howefield on 2016-11-10
> **adfh said:**
> Ubuntu offers multiple packages to pull in Flash, but they all seem to pull in the 11.2.202.644 version. My understanding is that the "adobe-flashplugin" method is the official method from the partner repository, but it, too, uses the older version.

adobe-flashplugin will give you

```
    - NPAPI: 11.2.202.644
    - PPAPI: 23.0.0.207
```

[https://launchpad.net/ubuntu/+source/adobe-flashplugin](https://launchpad.net/ubuntu/+source/adobe-flashplugin)

Which browser are you using it with ?

---

### Post by adfh on 2016-11-10
Primarily Firefox at the moment.. so options at the moment it would seem are from what's said:
* Using a NPAPI / PPAPI shim to get v23
* Using the Adobe Labs tarballs to get v24

---

### Post by deadflowr on 2016-11-10
> How have people cleanly tried the new version, or have you just been extracting the tarball manually?

That is the only way to get the newly updated beta version, as it's not going to make it into the Ubuntu update system any time soon.
It still has quite a bit of work.
(No gpu 3d accel nor drm support, currently.
Personally drm support is one of the few reasons I still use 11.2 on Firefox (need [hal]("https://launchpad.net/~flexiondotorg/+archive/ubuntu/hal-flash") to actually utilize the drm support))

reference on the new beta version and how to get it:
[http://blogs.adobe.com/flashplayer/2016/08/beta-news-flash-player-npapi-for-linux.html#sthash.laRm9Ulq.dpbs]("http://blogs.adobe.com/flashplayer/2016/08/beta-news-flash-player-npapi-for-linux.html#sthash.laRm9Ulq.dpbs")

---

