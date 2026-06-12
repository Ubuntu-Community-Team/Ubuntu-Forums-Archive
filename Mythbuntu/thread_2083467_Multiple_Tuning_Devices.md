---
title: "Multiple Tuning Devices"
date: 2012-11-12
forum: Mythbuntu
---

### Post by TheFuzz4 on 2012-11-12
Hey there everyone,

I just wanted to make sure that I set this up properly.  So for the last year I've had a Hauppage 2250 card with the dual tuner running in my backend I've used this for tuning in the basic of basic Comcast cable (Everything over the ClearQAM)  Last week I decided it was time to ramp it up and I ordered the HD Homerun Prime and got a cablecard from Comcast (BTW everything works on it just fine except for the Music Choice and the Premium channels) After an involved weekend I finally have my lineups back to where I want them.  This involved my wife and I spending some time in the Database as well as schedules direct going through and dumping out everything that was either in SD and had a HD counterpart or that we just didn't have or want.  So now that all of that is done in my channels table in the DB I do have some duplicate channels because there is a ClearQAM channel as well as a prime channel.  I was just wondering if say for example I went to my local channel 9 which comes in HD on both paid and ClearQAM if the myth will just choose a free tuner or something else?  Also when it comes to recordings will it give preference to one tuner over the other?  Thanks for your help with this in advance and there is a different method that I should use with the two different tuning devices please let me know.  Thanks.

---

### Post by dannyboy79 on 2012-11-12
when you setup the recording schedule you can choose which tuner it should use. As far as setting a preferred tuner for live tv I am not sure on that one, I am pretty sure it will just pick a free tuner.

---

### Post by NewAmercnClasic on 2012-11-13
Are Music Choice and the Premium channels not working due to DRM restrictions?  Which Comcast cable card do you have (also did you need one for each tuner)?

---

### Post by TheFuzz4 on 2012-11-13
> **NewAmercnClasic said:**
> Are Music Choice and the Premium channels not working due to DRM restrictions?  Which Comcast cable card do you have (also did you need one for each tuner)?

That is the best that I can come up with.  When I go to the channels all I get is just a black screen.  

So as to my original post what I ended up doing was setting up priorities on each of the tuners.  For the HD Homerun I setup 3 priorities for each tuner for both recording and live and then I setup priorities on the Hauppage card as well.  Now this way when we start to watch LiveTV we will go to a particular tuner depending on the channel and hopefully now it will also start recording on a different tuner instead of the one that I'm using, after all I now have 5 tuners in there, the least myth can do is leave me alone while I'm watching livetv :).  I hope that this will also help fix the problem where if no one presses a button that it doesn't jack up the recording schedules.  More to come on that.

---

### Post by TheFuzz4 on 2012-11-14
> **NewAmercnClasic said:**
> Are Music Choice and the Premium channels not working due to DRM restrictions?  Which Comcast cable card do you have (also did you need one for each tuner)?

Also I just got a M tuner card and nope you only need 1 card for all 3 tuners.

---

