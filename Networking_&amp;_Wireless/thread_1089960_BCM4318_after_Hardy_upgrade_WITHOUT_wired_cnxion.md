---
title: "BCM4318 after Hardy upgrade WITHOUT wired cnxion"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by alnilamski on 2009-03-07
Hi,

I just upgraded from Dapper to Hardy. Big jump, I know - I was holding out precisely because of how much trouble it had been to get my wireless working in the first place. Many of us know how troublesome BCM4318 cards can be.
Also, my desktop is running semi-gutted so I would like to avoid if at all possible having to take it downstairs to give it a wired connection.

So I had it going with ndiswrapper before, and I also only ever got it to work with WICD as a network manager (like it better anyway). After the upgrade, ndiswrapper ostensibly still had a working driver.

A thing came up telling me that there were "restricted" (?) drivers for the BCM4318 and I could enable them; of course this needed a connection, and I found out where it was trying to get that package from and got the .deb from another computer; even THAT package said it wanted to fetch some files, so no go.

So now WICD is not finding any networks, despite having reinstalled it AND wicd from .deb files.

Jecos on [this thread]("http://ubuntuforums.org/showthread.php?t=738216&page=4") said I should blacklist b43 and ssb as well as bcm43xx. I did, and no luck.

Anyone know how I can get a bcm4318 working again after Dapper->Hardy WITHOUT a wired connection?

---

