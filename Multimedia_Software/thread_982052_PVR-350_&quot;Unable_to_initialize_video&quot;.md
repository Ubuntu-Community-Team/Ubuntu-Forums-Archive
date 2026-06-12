---
title: "PVR-350 &quot;Unable to initialize video&quot;"
date: 2008-11-14
forum: Multimedia Software
---

### Post by musiseb on 2008-11-14
Hi.

I'm getting a message "Unable to initialize video".
I have a PVR-350 card. I did follow the HOWTO on Gutsy. All the checks I run work fine. 

When I run the command

cat Silhouet2001.mpeg > /dev/video16

I can see a video on my TV out with a big black box on top. 
I did add "deb [http://ppa.launchpad.net/superm1/ubuntu](http://ppa.launchpad.net/superm1/ubuntu) hardy main" to my sources.list file and I run a command:

$ sudo aptitude update && sudo aptitude safe-upgrade

This did not solve the problem. Is there something else I'm missing? I can watch TV when I turn off the PVR-350 hardware output in the Myth Setup, however the output has very poor quality.
I would appreciate all your help. Thanks.

---

### Post by musiseb on 2008-11-14
> **musiseb said:**
> Hi.

I'm getting a message "Unable to initialize video".
I have a PVR-350 card. I did follow the HOWTO on Gutsy. All the checks I run work fine. 

When I run the command

cat Silhouet2001.mpeg > /dev/video16

I can see a video on my TV out with a big black box on top. 
I did add "deb [http://ppa.launchpad.net/superm1/ubuntu](http://ppa.launchpad.net/superm1/ubuntu) hardy main" to my sources.list file and I run a command:

$ sudo aptitude update && sudo aptitude safe-upgrade

This did not solve the problem. Is there something else I'm missing? I can watch TV when I turn off the PVR-350 hardware output in the Myth Setup, however the output has very poor quality.
I would appreciate all your help. Thanks.

When I'm rebooting the system I see Mythbuntu logo on my TV through the S-Video.
I tried to install Fedora with MythTV before, but I had similar issues with the TV out not working. With Mythbuntu at least the initial install was fairly simple. I already spend few weeks trying to figure this out. Thanks.

---

