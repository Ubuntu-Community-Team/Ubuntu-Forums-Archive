---
title: "schizophrenic network problems"
date: 2006-01-31
forum: Networking &amp; Wireless
---

### Post by polkadotchickens on 2006-01-31
I'm running breezy on a laptop, and I've set up both my wired and wireless connections just fine, using some of the directions posted in here.  The problem is, sometimes they just quit working.  One, the other, or both.  For no real reason, apparently.  I often can't immediately tell, either, as gaim doesn't kick me off when this happens, or at least, it acts like it still has a working connection even though it doesn't.  When I run network-admin to try and fix it, sometimes deactivating the devices and reactivating them works, but not always.  Usually it eventually (minutes or hours later) restarts on its own and works fine, if deactivating doesn't do it.  I don't understand this problem at all, and it's hideously frustrating.

I've also discovered a problem with my network-admin through all this messing around and hoping my internet will work: it doens't save my profiles.  I have to tell it at least half a dozen times to create a new one before it does, and then it often forgets the configuration I had put in that profile.  Also, when I start it, it doesn't go to the profile I would like to set as default, or to any profile actually, but instead to one where the location box is blank.  Is this a problem with breezy in general, or something weird with my computer?

Thanks a lot, hope someone can help.

---

### Post by Nephiel on 2006-01-31
Same here. On my Breezy, wireless connection drops randomly for no reason.
I have a laptop with both wired and wireless cards built-in. Wired ethernet works flawlessly, but wireless does not. Disabling and re-enabling the interface with network-admin once, or twice at most, tends to fix it.

But the most annoying thing is that network-admin does not behave as it should.
-I configured both wired (eth0) and wireless (eth1) interfaces with static IP, and network-admin would always choose either eth0 or none as the "default gateway device" with every reboot.
-I wanted to use primarily wireless, so I disabled the wired interface eth0, but network-admin will re-enable it and bring it up with every reboot as long as it has an IP assigned, completely ignoring the /etc/network/interfaces file (there is no "auto eth0" entry on it) :confused: On top of that, then it chooses eth0 as the default gateway device :mad: 
-Network-manager and wifi-radar didn't help at all.
-The only way I found to have static IP eth1 wireless working at startup was to disable AND unconfigure eth0 so the only configured interface remaining is eth1. But even then the wireless connection keeps on dropping randomly.

Wired ethernet works fine. 

Any suggestions?

---

