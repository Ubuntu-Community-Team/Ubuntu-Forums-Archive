---
title: "Loosing Internet Connection"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by u0noob0u on 2009-08-02
I'm not sure if this is the correct location to ask for help with my issue.  But I'm loosing connection about 5 to 10 minutes after I start a Torrent.  I'm running moblock and ktorrent and Im running ubuntu hardy 8.04.  My connection drops off and i can't get my PC back on line untill I reboot the pc.  I'm new to linux but I would like to make it my OS that I run on all my computers at home...  Sorry if this is in the wrong forums, but I sure can use your help.  Thanks

UPDATE:  I tried Downloading a torrent with out moblocker and it works just fine.  So i'm thinking its a setting or something in Moblocker.  Can anyone help me set this up please.

---

### Post by jre on 2009-08-02
Please check /var/log/blockcontrol.log and /var/log/moblock.log (or post them her in CODE tags).

I could imagine that MoBlock is not running properly in the first place (therefore everything is working), then the blockcontrol watchdog detects this problem and restarts blockcontrol. Then Moblock is working just fine, but probably just lacks some configuration to allow certain traffic.

If you find out which IP or port is unnecessarily blockedby MoBlock you can whitelist it. Have a look at [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock) to learn how to do that. Using the GUI mobloquer makes this quite easy - just watch the logfile and right click on the appropriate lines there.

---

