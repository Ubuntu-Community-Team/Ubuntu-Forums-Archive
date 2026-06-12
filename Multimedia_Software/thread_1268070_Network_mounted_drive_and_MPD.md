---
title: "Network mounted drive and MPD"
date: 2009-09-16
forum: Multimedia Software
---

### Post by adam_kimber on 2009-09-16
Hi. I have a media server that has my music on it so both my lounge box and my office box can access it. The box is mounted to my home directory using NFS. It uses the name.local protocol in the fstab to mount each time as my router is junk and does not map by MAC address and static IPs failed to work at all and I cannot be bothered to faff with that anymore. 

I have two problems which I think might be related. 

1) If I reboot the router whilst my office machine is on all is good apart from MPD. It refuses to reconnect. It claims nothing is there whilst actually if i ls or go to it in nautilus the network drive is happily mounted. 

2) If I reboot the office machine MPD sometimes fails to get all the tracks in the network folder. I currently have less than half listed. Restarting MPD does not do anything. The only thing I have found that gets it to work is a full rebuilt of the DB. Which is not fun as it takes ages. On top of which happens "randomly".

Suggestions? If its "replace your media player as MPD does not work well in this setup" then I am after something like sonata. I wish sonata had a way of playing natively without using MPD. It would be the perfect player then. (I have numerous issues with MPD on Ubuntu, whether these exist on other distros I don't know). 

Thanks for your help.

---

