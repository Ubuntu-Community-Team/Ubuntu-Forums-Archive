---
title: "Kodi 16.1 jervis install on ubuntu 16.4"
date: 2016-05-02
forum: Multimedia Software
---

### Post by nat10 on 2016-05-02
Hi,

I'm new to this forum and linux, I have recently updated from 12.10 to 16.04. I have installed kodi 16.1 using this guide

To install a beta/unstable version of Kodi you must first add the unstable repository, then install XBMC. Use ppa:team-xbmc/ppa

sudo add-apt-repository ppa:team-xbmc/xbmc-nightly

sudo add-apt-repository ppa:team-xbmc/ppa

sudo apt-get update

sudo apt-get install kodi

Note that if you have any addons (such as PVR clients), these must be updated as well (they will not be updated automatically):

sudo apt-get install kodi-pvr-mythtv

It has loaded up fine, but I'm having trouble installing addons. I've  tried to install sportsdevil as I would on my android box but the set up  is totally different. I've had a message saying that unknown addons are  blocked for security, how can I allow these to be added?
Are the addons installed from the terminal?
All the guides online show the old kodi screens where the ubuntu 16.4 is derfferent.
If someone has a guide on how to install addons like sportsdevil and phoenix that would be great.

Thanks

Nat

---

### Post by jawilljr2 on 2016-05-02
It looks like you accidentally install Kodi alpha (17) with this line:

```
sudo add-apt-repository ppa:team-xbmc/xbmc-nightly
```

To install Kodi all you need is is the ppa:team-xbmc/ppa PPA.

To be sure please post the output of:

```
apt-cache policy kodi
```

Below is the ouput on my box:

```
kodi:
  Installed: 2:16.1~git20160424.1410-final-0wily
  Candidate: 2:16.1~git20160424.1410-final-0wily
  Version table:
 *** 2:16.1~git20160424.1410-final-0wily 0
        500 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ wily/main amd64 Packages
        100 /var/lib/dpkg/status
     15.1+dfsg1-3 0
        500 http://us.archive.ubuntu.com/ubuntu/ wily/universe amd64 Packages
```

---

