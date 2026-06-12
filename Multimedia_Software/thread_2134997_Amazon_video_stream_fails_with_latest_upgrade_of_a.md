---
title: "Amazon video stream fails with latest upgrade of adobe-flashplugin for 12.10"
date: 2013-04-12
forum: Multimedia Software
---

### Post by ajlewis2 on 2013-04-12
There was an upgrade of adobe-flashplugin 11.2.202.280.  After the upgrade I got an error message that I needed to update the flash player when I tried to watch streaming videos on Amazon Prime.  

I removed that version of the plugin and found the previous version at [https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.2.202.275-0quantal1](https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.2.202.275-0quantal1)  This is a tar.gz file and not a deb.  I used the i386 version of libflashplayer.so and put it into ~/.mozilla/plugins/

When I opened a video in Amazon prime I first saw an indicator that the player was being updated and then the video once again was working.

Reported bug at launchpad.

---

### Post by ajlewis2 on 2013-04-24
At some point Amazon must have fixed the problem. There have been no more upgrades of flash, but the version 11.2.202.280 of the plugin now updates at Amazon and works.

---

