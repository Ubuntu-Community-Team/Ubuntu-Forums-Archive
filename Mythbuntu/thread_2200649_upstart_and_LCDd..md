---
title: "upstart and LCDd."
date: 2014-01-20
forum: Mythbuntu
---

### Post by Steve Goodey on 2014-01-20
Hello,

LCDd has a configuration file LCDd.conf. I have an altered version with my driver name and driver path in /home/steve/lcd/ so that on any upgrades/changes it doesn't get overwritten.

The default home for LCDd.conf is in /etc. 

Now I can either soft link /etc/LCDd.conf to /home/steve/lcd/LCDd.conf

Or another way I've seen is to amend /etc/init.d/LCDd and change the line so that configfile=${etc}/LCDd.conf to configfile=/home/steve/lcd/LCDd.conf

Now apart from the fact that /etc/init.d/LCDd does not have that line is there a "proper" way to do this?

Hope this makes sense and thanks for any answers/suggestions.

Steve.

---

