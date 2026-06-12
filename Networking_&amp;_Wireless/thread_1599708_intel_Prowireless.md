---
title: "intel Pro/wireless"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by fishr on 2010-10-18
I am new to ubuntu, so this might be easy but I am having problems. I'll start at the beginning. 
Installed lucid on an old laptop. Everything worked as it should except wireless drops out constantly.  
Work perfectly on this computer with XP. Still working on other computers with win7, XP.
Tried just about everything. 
In the end un-installed network manager and I am now running wicd. 
The problem I have is a my wireless driver is unclaimed. I can get it working with the following code:
sudo modprobe --verbose iwl3945

This "claims"  the wireless and wcid works perfectly. However if I restart I lose the card again. I have to type the code again in terminal for wireless to work.

My question is how can i get the drives to install permanently.

Thanks in advance  

If needed: When i enter the code i get the following:
sudo modprobe --verbose iwl3945
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
insmod /lib/modules/2.6.32-25-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/2.6.32-25-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/iwlwifi/iwlcore.ko 
insmod /lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko

---

### Post by fishr on 2010-10-31
Ok, So not having any replies , got me a little worried. 
But maybe it was to easy to waste time on.
For those who may have the same problem, this is how i fixed it.
For the experts please tell me if this is wrong.
I edited the /etc/modules file. 
To do this I used
gksudo gedit /etc/modules

and in the file added teh line
iwl3945

Now it works.

---

### Post by Iowan on 2010-10-31
I have an older laptop (maybe with the same chipset) that I'm considering dualbooting. I might get the opportunity to try out your fix. Thanks.
Consider marking the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help others find your solution. :)

---

