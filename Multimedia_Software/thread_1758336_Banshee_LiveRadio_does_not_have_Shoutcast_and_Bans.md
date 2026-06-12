---
title: "Banshee: LiveRadio does not have Shoutcast and Banshee cannot see UPnP (11.04 Natty)"
date: 2011-05-14
forum: Multimedia Software
---

### Post by Routhinator on 2011-05-14
Ubuntu 11.04 has given me more woes than any previous version of Ubuntu at this point, but being music-less is really getting to me.

Banshee cannot access my PS3-Media-Server UPNP box, or see it. The radio station fetcher cannot retrieve streams as it gets a network error. The LiveRadio plugin does not have Shoutcast in it, even though the package description clearly states it should. In fact, the only plugin in LiveRadio that works is Magnatune.. and don't get me started on how much I dislike a service that plays half a song and cuts it off.

Repeated attempts to try finding solutions to these issues keep leading me back to outdated and dead-end forums from mid 2010, with bug reports that claim to be fixed, and none of the steps seem to correct my issues.

I have also tried just simply wiping and reinstalling banshee and it's plugins, with no success. I have attempted to modify the smb.conf file with the recommended line as mentioned in [https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/498697](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/498697) to no avail. Manually attempting the connection to the UPNP server does not work either.

Help? I need some music.. this is killing my productivity.

---

### Post by flick on 2011-06-13
Installing/updating Banshee from the Banshee Team PPA provided me with a Banshee whose Radio Station Fetcher plugin actually worked with Shoutcast. :) 

Quick link : 

[https://launchpad.net/~banshee-team/+archive/ppa](https://launchpad.net/~banshee-team/+archive/ppa)

---

