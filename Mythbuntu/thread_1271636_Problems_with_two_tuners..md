---
title: "Problems with two tuners."
date: 2009-09-21
forum: Mythbuntu
---

### Post by Tim L on 2009-09-21
Problems with two tuners.

I am using MythBuntu 9.04 with two tuners. One is a Hauppauge WinTV PVR-150 with the composite 1 input which is then connected to a SKY pay-to-view satellite box and a Hauppauge Nova-S-Plus for free-to-air satellite TV. I can get one or the other to work as long as there is only one installed. I can get both to work at the same time during setup, but as soon as the backend re-boots the autodetect in the Capture Card Setup switches the board so that for the WinTV PVR-150 shows the “Probed info: Nova-S-Plus DVB-s [cx8800]”. As a result Mythtv stops working. I then have to remove one board and set up Mythtv again. I think what I need to do is stop the auto detect once setup is complete, but do not know how to do it.  I have found a few things on the web about turning off autodetect but none seem to resolve my problem.

---

### Post by KillerKiwi on 2009-09-21
This should sort it out.. try the python script in the issue

[https://bugs.launchpad.net/ubuntu/+source/mythbuntu-meta/+bug/370696](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-meta/+bug/370696)

---

