---
title: "Multiple back and frontends"
date: 2008-07-02
forum: Mythbuntu
---

### Post by pmbsa on 2008-07-02
Hi, I am pretty new to all this and I seem to be struggling with some basics here, hopefully somebody can fill in some blanks for me.

I have a primary backend (with a single tuner) and a few secondary backends (also with tuners). I can get the tuners working fine on the backends (all) provided, on each backend, I leave the IP address setting for the primary backend set to the local IP of the bckend concerned. The moment I change this setting to point to the actual primary backend then the tv function stops and I get this helpful error in my frontend log "sh: gggg: not found".
I dont get any connection errors when starting the frontend so I assume the backends are connecting but I get no joy from the TV function.

Could somebody maybe fill me in on the purpose of a primary backend? Should I be pointing all my frontends to this primary? (or at least any front ends that dont have a local secondary backend?)

thanks
Paul

---

### Post by Archmage on 2008-07-02
> **pmbsa said:**
> Could somebody maybe fill me in on the purpose of a primary backend? Should I be pointing all my frontends to this primary? (or at least any front ends that dont have a local secondary backend?)

Your primary backend should be the machine with many turners that is hopefully on all the time and is recording every show in the TV.

The frontends are for watching only.

I find the idea of having secondary backend a little stupid (they need to be on to record something. (okay you can start them even automatical, but why should you bother with it?)

The only good thing on them is, that they can do some comercial flagging/transcoding when they are turned on.

At least for me it is: ONE backend, a few frontends and most of the time not watching live, because you can do so much more with a finished recording (speed up, pause, rewind, skip forward - e.g. comercials and so on.)

---

### Post by Eldis on 2008-07-03
I really new to this aswell and you say the backend could and should record all shows on tv luckily here there aren't that many of them maybe 4-5 muxes. How long should one setup the shows to be kept ? I know it's pretty much up to me but what would be a reasonable time and how much HDD space would that need?

Would channel changing be faster from the frontend with let's say 3-4 cards recording everything ? Since normally when you change channel on myth it takes a few seconds to happen.

---

### Post by Archmage on 2008-07-03
I'm sorry for the misunderstanding. But of course the backend should only record showes that you like. Recording everything on TV would be a little to much, onlike you think that you would want to watch everything.

You simply tell Mythtv what to record. You can record shows, search for keywords and so on.

E.g. you could tell Mythtv to recrod every show of the show "Jericho" and everything that has the word "nuts" in the the description and every new show of Southpark (you can set it up that it wont record reruns) and so on.

So you would need at least on turner to record. Since Mythtv 0.21 (included in Hardy) you can even record up to five showes at once on one mux (good for back-to-back episodes when you start the record a little early and stop a little late to capture everything or if they have more than one channel on one mux).

Deepending on the setting on if you are transcodeing a show can use round about 1 GB for one hour in PAL-qualtiy and 4 GB for HD-qualtiy.

But normaly you wouldn't bother with keeping the shows, since you can tell Mythtv that is should delete the old shows (and also put keep an eye on the priority and the watched status so that your favourite shows wont be deleted too soon).

As you can see, you wont need to record everything. The changing time of the channel wont be incresed, because this is the way Mythtv works (it records first and than shows it, therefore Mythtv is more for watching captured showes than live-tv.)

---

### Post by volkswagner on 2008-07-03
All slave backends and frontends should point to the master ip for the database location. there is a separate setting to allow recordings to be stored local or on the master.  Depending how you set everything up, you may try deleting your tuners.  Then add them once you have all machines pointing to the master ip for database location.

---

