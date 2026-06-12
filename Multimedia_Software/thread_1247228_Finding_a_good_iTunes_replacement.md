---
title: "Finding a good iTunes replacement"
date: 2009-08-22
forum: Multimedia Software
---

### Post by TheK3vin on 2009-08-22
I've been trying out some of the more popular iPod/podcast managing programs available for Linux, such as Banshee, Listen, gtkpod, etc., but I have yet to find what I would consider the perfect app for proper podcast consumption.  Banshee, for example, allows you to subscribe to podcasts but doesn't automatically download them and *doesn't save your place in them*.  Then, when you do download them manually, it puts them in your iPod's music section and doesn't allow you to save your place in the iPod either.  I can't find anything that functions as well as iTunes- does it even exist?

---

### Post by Major_Kong on 2009-08-22
Probably not... Have you tried songbird ?

[http://getsongbird.com/](http://getsongbird.com/)

---

### Post by Elviswind on 2009-08-22
I'm pretty sure you can setup Banshee to automatically download all podcasts . . . actually, I'm fairly certain because I changed the option to download no podcasts.  I don't know about your other questions though . . . don't own an iPod and have never used iTunes.

---

### Post by shawnfain on 2009-08-23
I agree. The new Amarok 2.x doesn't work well in Jaunty, The old 1.4 is really nice, if you download and install the ppa, but it won't automatically download podcasts. There is an option for "download when available" and you can set it to automatically CHECK for new episodes, but it just doesn't download them until you click each one, which defeats the purpose. I don't have time to download a 30 minute video before going to work, I need it to do that overnight.

Gpodder will download them allright, but only deletes UNPLAYED episodes after 7 days. If you have an hourly news show, you wind up with 24 x 7 of them in your directory, and have to go manually delete them all since you're not likely going to listen to every single hour of ever single day. And you can't say, keep only last episode.

I've tried Banshee - won't actually delete  the episodes and is buggy
Exaile - no podcast ability that I could find
Rhythmbox - can't remember what didn't work

It's just amazing how little good support for podcasts there are for linux.

Since I can't sync my iphone anyway (I know about Airshare and jailbreaking and openssh, but they don't work with the ipod app etc, and it's too clunky to do all that manually, one song at a time etc.), I'm just using itunes on my mac to sync podcasts and music.

I'd like to at least be able to listen to and watch podcasts on my ubuntu machine.

Come on guys! Help us break free from non-open-source podcasting! :-)

---

### Post by shawnfain on 2009-08-23
Just tried out songbird, and it will download automatically. But it downloads ALL the episodes, and if you can limit that or set any retention schedule, I didn't see it.

I thought the purpose of a podcast aggregator was:

1. Automatically check for new episodes - why make the human do it?
2. Automatically download new episodes - why subscribe if you don't want the latest episode?
3. Automatically prune the podcast folder - why would you want to keep countless episodes? Either ones you've heard or ones that you didn't get around to that are now two weeks old.

iTunes does this automatically. For all the complaining everyone does about iTunes shouldn't they at least include the functionality it has? Do podcast aggregator developers actually listen to podcasts regularly?

I'm sure there are lots of ways to do this with a python script or cron, or some other command line app, but I'm just not interested in doing that. 

If anyone has found a linux app that will do the above 3 things, please post it here.

Thanks

---

### Post by Major_Kong on 2009-08-23
Yeah...i've checked the songbird roadmap, and unfortunately they delayed full podcast support... so they're well aware of the problems, but don't see it as prioritary.

---

### Post by tyblu on 2009-08-23
doubleTwist will someday do this :P

---

### Post by skyjacker on 2009-08-23
> **Major_Kong said:**
> Probably not... Have you tried songbird ?

[http://getsongbird.com/](http://getsongbird.com/)+1 for Songbird

---

### Post by blade1950 on 2009-08-31
For me, Songbird does the trick. Banshee (frequently crashed), Amarock (remined me of a virus), etc just didn't fit the bill for overall performance and ease of use etc.

---

### Post by gordintoronto on 2009-08-31
> **shawnfain said:**
> 1. Automatically check for new episodes - why make the human do it?
2. Automatically download new episodes - why subscribe if you don't want the latest episode?
3. Automatically prune the podcast folder - why would you want to keep countless episodes? Either ones you've heard or ones that you didn't get around to that are now two weeks old.
If anyone has found a linux app that will do the above 3 things, please post it here.

Thanks

Have you tried Miro?

---

### Post by gf_gollum on 2009-08-31
As a new Ubuntu user - I just installed aTunes [http://www.atunes.org/](http://www.atunes.org/) - and it works fine for me. It handles podcasts, radio etc - and includes all the codecs you need out of the box.
Graham

---

### Post by acornbrain on 2009-08-31
Yes, I too would be very interested in the itunes solution.

My plan is to get both computers running Ubuntu. I'll let Windows live on life-support on one of them, behind a dual-boot partition.

So I need to convince my wife that Ubuntu can do everything she needs the PC for:

Web browsing- check
Remote Desktop connection- check
Word processor- check

the thing that worries me is itunes. she uses it to sync her ipod and has some automatic podcast subscriptions/downloads going. I got rythimbox to recognize her ipod with gtkpod. But if she can't get all the functionality she's accustomed to with itunes, as well as still be able to buy from the itunes store, then she will be constantly booting in with Windows, and she is not going to want to reboot into Ubuntu after she's done with itunes.

---

### Post by gf_gollum on 2009-09-05
Thanks for all the suggestions - I'll work my way through them. Nice to know I'm not alone in identifying this gap. 
Graham

---

