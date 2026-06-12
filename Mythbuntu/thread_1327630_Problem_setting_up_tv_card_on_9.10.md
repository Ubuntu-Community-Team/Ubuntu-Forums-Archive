---
title: "Problem setting up tv card on 9.10"
date: 2009-11-15
forum: Mythbuntu
---

### Post by Elv13 on 2009-11-15
Hi, I just did a fresh install of Mythbuntu 9.10. I configured my tvcard (saa7134) with the right tuner and model in /etc/modprobe.d and it work. I can use it in tvtime or mplayer. Now, I want to use it in mythtv, but I failed until now. 

I opened mythbackend setup, added a tvcard, selectionned /dev/video0 and the "television" input. When I change thing in the backend config, I ear the sound in my speaker form the TV during 1/5 second, so it do something, but when I want to watch TV in frontend, I get:

"mythtv is using all inputs but there are no active recordings"

I am kind of new to mythtv, I played with it in the past, but never that much, I never really used it so I am a little lost. What's wrong? I am on 32bit by the way if it can help and I did not edit any settings other than that one.

EDIT: Look like I am affected by this bug [https://bugs.edge.launchpad.net/ubuntu/+source/mythtv/+bug/478048](https://bugs.edge.launchpad.net/ubuntu/+source/mythtv/+bug/478048) . It explain why MythTV is not able to scan/see channal without scheduledirect

---

### Post by nickrout on 2009-11-15
did you go through ALL the steps in mythtv-setup?

ie 

[LIST=1]
[*]capture card
[*]video source
[*]input connection
[*]channel editor
[/LIST]

Sounds from your description that you might not have got all the way through the list.

See [http://www.mythtv.org/wiki/User_Manual:MythTV_structure](http://www.mythtv.org/wiki/User_Manual:MythTV_structure)

---

