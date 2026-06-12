---
title: "Intermittent MythTV Frontend Connections - A Workaround with gupnp"
date: 2012-01-23
forum: Networking &amp; Wireless
---

### Post by tehowe on 2012-01-23
I've been having a problem with MythTV connectivity ever since I installed it.

It's been intermittent (eg; frontends say 'No UPnP') across my local network for months and it's seemed to come and go when updates get pushed across the Mythbuntu PPA. It's been really annoying.

But no longer - I discovered **if you run the UPnP 'Universal Control Point' from the gupnp package it will keep the MythTV UPnP connection open!**

You can install gupnp from the Software Centre or from the command line

```
sudo apt-get install gupnp
```Then you'll find the UPnP Universal Control Point under your Gnome 'Applications/Programming' menu. Run it on your MythTV server and leave it running.

I don't know where the problem lies. MythTV? UFW blocking multicast? (probably not, since the problem's there even when UFW is disabled) My DLINK DIR-628 router? Ubuntu Studio 11.04? But I'm posting this because maybe it will work for you as well.

---

