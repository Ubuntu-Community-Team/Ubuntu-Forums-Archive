---
title: "AR928X (ath9k)problems."
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by Post Monkeh on 2010-01-23
i've been using ubuntu since intrepid, but since upgrading to karmic i've been having problems with my wireless card. to be honest it was never *perfect* but where before i would maybe get one or two disconnections a  week, it now has kittens any time i ask it to do anything other than load a simple web page. it seems to be directly related to the traffic going through it, the more i'm doing, the quicker it freaks out. the problem is that once it disconnects, it won't reconnect until i rmmod/modprobe the driver.

i've tried installing the compat wireless drivers but it doesn't seem to make any difference, does anyone have any other suggestions?

failing that, i have made a script that removes the ath9k driver then reinstates it a few seconds later. is there any way to make this script initiate when my wireless connection drops?

---

### Post by bkratz on 2010-01-23
> **Post Monkeh said:**
> i've been using ubuntu since intrepid, but since upgrading to karmic i've been having problems with my wireless card. to be honest it was never *perfect* but where before i would maybe get one or two disconnections a  week, it now has kittens any time i ask it to do anything other than load a simple web page. it seems to be directly related to the traffic going through it, the more i'm doing, the quicker it freaks out. the problem is that once it disconnects, it won't reconnect until i rmmod/modprobe the driver.

i've tried installing the compat wireless drivers but it doesn't seem to make any difference, does anyone have any other suggestions?

failing that, i have made a script that removes the ath9k driver then reinstates it a few seconds later. is there any way to make this script initiate when my wireless connection drops?

Hopefully maybe this thread will help.

[http://ubuntuforums.org/showthread.php?t=1309605&highlight=AR928X](http://ubuntuforums.org/showthread.php?t=1309605&highlight=AR928X)

See post 5

---

### Post by Post Monkeh on 2010-01-23
i'd read a lot of posts about installing the backports, but a lot of people said it didn't help. that's the first i've read about the change to the conf file though.

seems to be a little better (sitting at around 40% which is good considering the layout of the house) hopefully it stays like this. thanks!

---

