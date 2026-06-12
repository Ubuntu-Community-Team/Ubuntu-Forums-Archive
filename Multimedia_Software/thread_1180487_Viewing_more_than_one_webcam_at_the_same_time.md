---
title: "Viewing more than one webcam at the same time"
date: 2009-06-06
forum: Multimedia Software
---

### Post by pitbullthe1st on 2009-06-06
Hi,

I am trying to setup my computer to monitor 3 webcams at the same time but I can only view 1 at a time.  They all work individually but I can't find a way to monitor them all on the same screen.  Is it passable to do this and if so how?  

I have tried using motion but I have not had any success it seams to freeze up one or more of the cams and the live stream is very pore quality and dose not work very often in fact I have only had 1 of the cams working through it and that was poorly.

The webcams are all different types (2 are cheap unbranded ones and 1 is an old creative labs) but they all work in cheese ok unless I try to use motion then I have to reboot before I can use cheese again or I get errors about bits missing and that it could not decompress properly even if I have killed the motion process.

I only need to use this from inside my network so there is no need ftp servers and I'm perfectly happy to use it over ssh like I am doing with cheese rather than http. Ether way would be ok as long as I can have all cams on 1 screen.

Thanks for your help in this matter.

---

### Post by SteveDee on 2009-06-08
> **pitbullthe1st said:**
> Hi,

I am trying to setup my computer to monitor 3 webcams at the same time but I can only view 1 at a time.  They all work individually but I can't find a way to monitor them all on the same screen.  Is it passable to do this and if so how?  

I have tried using motion but I have not had any success it seams to freeze up one or more of the cams and the live stream is very pore quality and dose not work very often in fact I have only had 1 of the cams working through it and that was poorly.....

If quality is bad with just 1 camera running with "motion" then you may need to tweek the config file some more (See: [http://www.lavrsen.dk/foswiki/bin/view/Motion/MotionGuideBasicFeatures#Capture_Device_Options_The_Basic](http://www.lavrsen.dk/foswiki/bin/view/Motion/MotionGuideBasicFeatures#Capture_Device_Options_The_Basic))

If the problem is with running more than one camera, it could be a bandwidth limitation (see: USB cameras take a lot of bandwidth... in the link above).

Also take a look at ZoneMinder: [http://www.zoneminder.com/](http://www.zoneminder.com/)

---

