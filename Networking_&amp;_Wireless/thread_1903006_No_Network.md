---
title: "No Network"
date: 2012-01-01
forum: Networking &amp; Wireless
---

### Post by styleruk on 2012-01-01
No Network, now that is something that should easily be solved, however, I've been at this for hours now with no luck.
I'm talking wired network here, not wireless.  Seems everyone has questions about wireless.
1) I have Ubuntu 11.10 (that is 2011).  64bit.

I've checked the cables works by plugging into my XP laptop.  So the cable is fine and ubuntu shows no network available.

2) Tried setting up manually with the local IP address etc...no go.

3) Have a spare pci nic, tried that and disabled the on-board network chipset in the bios....no go with the new card that always used to work.

4)  I know, run off a boot disk.  So download latest ubuntu with my increasingly useful XP laptop and boot up on that...still no network!

5)  Have old 9.04 ubuntu disk so install that next to my existing ubuntu...nope, does not want it.

Kinda reluctant to completely clean install as I have so many tweaks and fixes for wine software etc... that it will take a week to set up again.

Not so fantastic on terminal commands but have tried these few things.

6) sudo service network-manager stop
 followed by start....still nowt

Now run out of ideas, I'm sure there are a million things I can try, at the moment easiest is to install XP and forget all my troubles but have been using ubuntu for years now and would like to fix it somehow.

Could it be my Bios somehow?  I've been through the bios and even reset it completely by taking out the battery etc... but there is nothing obvious there.

7) Tried desperately to add cd of latest ubuntu to repositories but did not update from that.  My thoughts were that it might re-install the network services for me but then if my other installs of ubuntu don't work either what else can it be?


Any help please?

Si

---

### Post by smouelhi on 2012-01-03
Same problem with an ethernet Intel card 82579LM and an e1000e driver (version 1.9.5).
My laptop is a Dell 6520 ....](*,)](*,)](*,)

---

