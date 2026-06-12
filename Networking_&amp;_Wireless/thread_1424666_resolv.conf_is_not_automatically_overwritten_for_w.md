---
title: "resolv.conf is not automatically overwritten for wireless"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by moepmoep on 2010-03-08
Hi,

I have a problem. For some reason my resolv.conf is not automatically overwritten when I use wireless. For a wired connection everything works fine. This is a problem when I am in a public network and do not know their dns-servers or worse in a university network where typically public dns-servers cannot be used either. 

I have checked whether any static settings are set but did not find anything, everything looks fine. I am using wicd, but the problem shows up no matter whether I use it with dhclient or dhcpcd. Furthermore I use reolvconf, but the /etc/resolv.conf is a symbolic link as it should be. I have been wondering whether this might be a problem of properly set rights, but then it should not work for a wired network either. 

The problem first showed up, after I had solved a similar problem for my wired network (but there the problem simply was a wrongly set static-constant in the wicd-settings). This seems not to be the case now. 

A first help would be if somebody could tell me how manually to ask the router what dns-server to use (in this case I could manually set the reolv.conf -- not very satisfying but at least working).

Any other suggestion in which file to look for possible errors would much be appreciated, since I feel out of options except for completely reinstalling kubuntu, which for sure would yield further problems :-(.

Thanks a lot,
moepmoep

PS: Okay, it seems it is not being overwritten for the wired connection either (just since the same dns-server always worked for all of my wired connections I never realized that). Furthermore it seems that resolvconf writes the proper eth0, wlan0 files into /etc/resolvconf/run/interface -- just does not seem to copy them properly into the resolv.conf. Has anybody any idea why this is so?

---

