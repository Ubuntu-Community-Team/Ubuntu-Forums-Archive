---
title: "internet connection problem - totally fedup"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by nimonika on 2010-01-01
I never had any problems with wireless connectivity, however since last few days I am having real nightmares. Every so often,my connection gets disconnected for no reason and I have to restart my laptop to get the connection back again. I cannot seem to figure out what has gone wrong in last few days that this has started to happen. I do not even know how to trouble shoot this problem and I also cannot afford to restart everytime I loose the connection.

Please can someone help.

Thanks

---

### Post by gordintoronto on 2010-01-01
Here's a wild guess: your next-door neighbour got a new computer for Christmas, with a wireless connection, and they are using the same channel as your router.  Try changing channels.  It's a setting in your router.

---

### Post by confusedstingray on 2010-01-01
gordintoronto is probly close. by any chance get a cordless phone a gift same problen took me a 3 weeks to figure this out. it was the phonebase to phone it seems that no matter what hz the phone. It is the phonebase to phone talk at 900hz if you want take your router off of auto channel and set it between ch 6 and 11 it is a trial and error

---

### Post by adam814 on 2010-01-01
In the meantime while you're figuring out the exact cause you might be able to get away with this to get your network back up without restarting:
```
sudo /etc/init.d/networking restart
```
Cordless phones do mess with wifi as well.  I had one that out of 80 channels the phone could use would always within 10 minutes find one that overlapped my router and knock out the connection.

---

### Post by phawnex on 2010-01-01
could be the actual wiring in your building too...

i lived in an apartment in downtown toronto, the channel changing worked for a bit then it would eff up again... then it stays on for days and screws up for days at a time even after changing channels and re-setting up the whole wireless network again.

if it doesnt work from what some of the other people are giving their advice through ubuntu, then try to talk with ur cable providers.  after i called mine they rewired some parts and worked flawless.

---

