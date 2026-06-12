---
title: "Banshee 2.0 Updates? Fixes?"
date: 2011-04-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Hedgehog1 on 2011-04-22
When I am running Natty, I am using Banshee 2.0

It plays my music fine, but it has a lot of goofy behaviors the earlier version of Banshee running in my 10.10 installs do not exhibit.

While Ubuntu and Unity get better every day as we get closer to release, Banshee ***seems*** unchanged to me. It still often does not save the last song played, and the song shown in the pull-down under the volume icon is always the previous song played, not the current one.

I know it does this and work around it; but it's not really putting the best foot forward for new Ubuntu users who expect this 'basic' (by todays standards) behavior to work.

**Does anyone know if Banshee will be ready for the big Natty release?**

Thanks,


***The 'musical' Hedge***

:KS

---

### Post by PaulW2U on 2011-04-22
> **Hedgehog1 said:**
> 
**Does anyone know if Banshee will be ready for the big Natty release?**

As ISO testing for the final release has started I doubt there will be many if any further fixes released until after 28th April.

For what it's worth banshee, along with several other applications, wouldn't even run on my 10.04 system which I installed just a few weeks after release. And they have remained that way ever since. :(

---

### Post by gnomeuser on 2011-04-22
Please file bugs found in Banshee. Bonus points for testing with the daily ppa first.

[http://www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/](http://www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/)

For the record my git compiled Banshee works just fine.

---

### Post by Hedgehog1 on 2011-04-22
> **gnomeuser said:**
> Please file bugs found in Banshee. Bonus points for testing with the daily ppa first.

[http://www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/](http://www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/)

**For the record my git compiled Banshee works just fine**.

Thanks for that - I am trying to use it 'like a new user' who will judged the distro based on the default applications.

However, for my system I will likely compile it.

---

### Post by gnomeuser on 2011-04-22
> **Hedgehog1 said:**
> Thanks for that - I am trying to use it 'like a new user' who will judged the distro based on the default applications.

However, for my system I will likely compile it.

Well I am on the Banshee team, so it makes sense to me to compile my own. My point was more that Ubuntu patches Banshee and packages it. Both can be the source of issues, e.g. the "move your music to /home/user/music" thing is entirely an Ubuntu addition. Typically the Ubuntu packages are not a source of issues but it is not impossible especially when they "add value". 

I would recommend simply using the daily ppa instead of compiling it as a normal user. It gives you all the benefits and none of the compiling. A fresh Banshee as code is changed and it is much easier to get things fixed due to the rapid feedback cycle. The only reason I do my own is for purposes for reviewing patches and well.. it gives me that fuzzy feeling inside.

Fear not we have excellent unit testing and high standards for code inclusion. Using the Dailies is perfectly safe and most times I would argue a better user experience than the releases (since distributions have a tendency care more about version number stability than actual stability).

---

### Post by Hedgehog1 on 2011-04-22
> **gnomeuser said:**
> ... Fear not we have excellent unit testing and high standards for code inclusion. Using the Dailies is perfectly safe ...

I do agree that high standards that have been maintained for Banshee!  The fact that your compiled version carries fixes for the issues I noticed means that the defect corrections are happening.

Thanks for all the hard work!

***The Hedge***

:KS

p.s. I would still like to see a more bug-free version of Banshee carried on the Natty pull, but the 'version carried' is out of the control of the Banshee team...

---

### Post by Hedgehog1 on 2011-04-22
** Double Post ** I hate it when I do that!

---

### Post by xebian on 2011-04-23
I find it odd that it doesn't want to accept drag & drop.

---

### Post by castrojo on 2011-04-23
> **gnomeuser said:**
> I would recommend simply using the daily ppa instead of compiling it as a normal user.

Ouchies. Any hope for a more stable PPA? 

(Even a PPA for dev releases is fine for me, dailies are too bleeding for me.)

---

### Post by mc4man on 2011-04-23
> **xebian said:**
> I find it odd that it doesn't want to accept drag & drop.
Not sure banshee is intended for such stuff - 

You can do single track playback either from a drag & drop launcher or a r. click option (nautilus-actions would work well

It's a bit less than ideal because I don't see a command to clear the system queue which would be the best way ( not uncommon in many of the current versions of players - amarok 1.4 was very good there w/ load, enqueue, append and play combos
*there is a gui enabled option to clear the system queue on quit but that's only semi useful

A command like this works ok for _single track play_ using the file to initiate from  a d&d launcher
banshee --play-enqueued  --hide --stop-when-finished-true  
or in NA a command of banshee, parameters of 
--play-enqueued  --hide --stop-when-finished-true %U
and a working dir. of  %d

---

### Post by gnomeuser on 2011-04-23
> **castrojo said:**
> Ouchies. Any hope for a more stable PPA? 

(Even a PPA for dev releases is fine for me, dailies are too bleeding for me.)

Trust me, the least problematic means of using Banshee is the dailies. Would you rather have point releases with weeks between your bugfixes or get them the next day.

We have never had a database corrupting problem in the dailies and the database format itself has been solid. We have tons of daily users, unit testing and high quality standards for code inclusion to keep us honest. 

A stable version number is not assurance of stability, that is.. broken distribution thinking.

Regardless naturally we have PPAs for the maintained released, the active development releases and dailies.

see:
[https://live.gnome.org/Banshee/CommonQuestions/TestingOnUbuntu](https://live.gnome.org/Banshee/CommonQuestions/TestingOnUbuntu)

---

### Post by Hedgehog1 on 2011-04-25
I am now running Banshee as carried in the Daily Build, and all but 1 defect (UI error, but not a show stopper) has been resolved.

I have reported it using bugzilla as outlined in the links. I even checked that it wasn't a duplicate!  I feel so empowered...


***The Hedge***

:KS

---

### Post by gnomeuser on 2011-04-25
> **Hedgehog1 said:**
> I am now running Banshee as carried in the Daily Build, and all but 1 defect (UI error, but not a show stopper) has been resolved.

I have reported it using bugzilla as outlined in the links. I even checked that it wasn't a duplicate!  I feel so empowered...


***The Hedge***

:KS

Rock on!

---

### Post by VinDSL on 2011-04-25
> **Hedgehog1 said:**
> I am now running Banshee as carried in the Daily Build, and all but 1 defect (UI error, but not a show stopper) has been resolved.

> **gnomeuser said:**
> Rock on!
Bwahahaha!  Are we giddy?!?!?  :D

Banshee is now warning me to "Please move your music to /home/vindsl/Music".

First of all, I don't have any music to move, and secondly, I have no such folder to move my non-existent music to.

When I right-click All Artists (0) or All Albums(0) in my non-existant music library - looking for a clue - Banshee disappears.  LoL!  

It doesn't even give me the courtesy of crashing.

Whatever!

In my experience, all media players suck!  Banshee is as good as any...

The devs are accessible and friendly!  :guitar:  Rock on!

---

### Post by taojian on 2011-04-25
Just moved to dailies; Banshee now using a fraction of the RAM it used to…

:)

---

### Post by gnomeuser on 2011-04-25
> **VinDSL said:**
> Bwahahaha!  Are we giddy?!?!?  :D

Banshee is now warning me to "Please move your music to /home/vindsl/Music".

First of all, I don't have any music to move, and secondly, I have no such folder to move my non-existent music to.


This specific insanity is not Banshee. It is an Ubuntu patch to Banshee and issues with it should be filed on Launchpad. Banshee does not support it.

> 
When I right-click All Artists (0) or All Albums(0) in my non-existant music library - looking for a clue - Banshee disappears.  LoL!  

It doesn't even give me the courtesy of crashing.

Whatever!

In my experience, all media players suck!  Banshee is as good as any...

The devs are accessible and friendly!  :guitar:  Rock on!

You can run with --debug to see what is going on. Bug reports are welcome ([http://www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/](http://www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/)).

---

### Post by gnomeuser on 2011-04-25
> **taojian said:**
> Just moved to dailies; Banshee now using a fraction of the RAM it used to…

:)

yeah plugging that massive hole in gio-sharp really made a big difference especially for cases where the Library Watcher is in use.

In fact Alan McGovern did some testing using the Mono 2.10 profiler and none of the Managed parts of Banshee leak any memory now. Any leaks that happen are in the underlying platform and the few remaining bits of C code in Banshee.

Additionally on my slow machine startup time is now half that of 1.6.x, and this includes those 7 secs initializing gtk which have not changed since then (and which Banshee can't do anything about). We even have further optimization open to us so progress is definitely going in the right direction.

---

### Post by VinDSL on 2011-04-26
> **gnomeuser said:**
> This specific insanity is not Banshee. It is an Ubuntu patch to Banshee and issues with it should be filed on Launchpad. Banshee does not support it. [...]
Thanks, for the insight, as always!

I bite my tongue (a lot) in these threads.  But when I read the OP's comment that all bugs have been fixed (except for one), the gag reflex set in.

It's like sticking a finger down your throat, eating a piece of rotten meat, or smelling flatulence on a crowded bus.

You just can't help but react to things like that, you know?  LoL!  :) 


> **gnomeuser said:**
> You can run with --debug to see what is going on. [...]
I'll try that.

That's how I do forensics on most proggies - start a proggie in cli - but I don't normally use --debug.

If I discover anything, I'll issue a report...  ;)

---

### Post by Hedgehog1 on 2011-04-26
> **VinDSL said:**
> ...I bite my tongue (a lot) in these threads.  But when I read the OP's comment that all bugs have been fixed (except for one), the gag reflex set in...

I guess I need to be more careful with my words - all the bugs that ***I Found***  (but 1) were fixed, and that one can be hidden (as it turns out) by turning off 'gapless playback'.

No truly complex system is ever bug free; but as long as the bugs don't affect me I am content.  Self centered, I know. But there it is.


***The 'Musical' Hedge***

:KS

---

### Post by gnomeuser on 2011-04-26
> **VinDSL said:**
> Thanks, for the insight, as always!

I bite my tongue (a lot) in these threads.  But when I read the OP's comment that all bugs have been fixed (except for one), the gag reflex set in.

It's like sticking a finger down your throat, eating a piece of rotten meat, or smelling flatulence on a crowded bus.

You just can't help but react to things like that, you know?  LoL!  :) 


I think it is quite valid, it might very well be that of all the bugs he has encountered only one remains. There wasn't a claim that Banshee is bugfree (hell we have +850 open bugs on Bugzilla currently, even I would not make that claim).

> 
I'll try that.

That's how I do forensics on most proggies - start a proggie in cli - but I don't normally use --debug.

If I discover anything, I'll issue a report...  ;)

Banshee has a number of useful parameters and if you read the article I linked earlier you will learn how to use them to investigate and collect information on a number of different issue types from crashers to performance. For the latter a new feature was just added (post 2.0, in the dailies) so that any query takes more than 500ms, when you run with --debug so if something is consistently slow in this respect it will be caught in using standard investigation technics.

---

### Post by gnomeuser on 2011-04-26
> **Hedgehog1 said:**
> I guess I need to be more careful with my words - all the bugs that ***I Found***  (but 1) were fixed, and that one can be hidden (as it turns out) by turning off 'gapless playback'.

No truly complex system is ever bug free; but as long as the bugs don't affect me I am content.  Self centered, I know. But there it is.


***The 'Musical' Hedge***

:KS

Yeah gapless is known to be problematic especially for last.fm. GStreamer is for all it's glory kinda hard to figure out when it goes wrong, luckily in most cases it just works (and in fact I devoted some time the past cycle simply to rip workarounds for old GStreamer bugs out).

---

