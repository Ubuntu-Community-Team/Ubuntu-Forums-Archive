---
title: "Go Back to 0.21"
date: 2009-11-27
forum: Mythbuntu
---

### Post by t3chn0b0y on 2009-11-27
Im having serious issues when editing video, the frames stick.
The same problem happens when fast forward & rewinding.. giving
me serious eye strain, headaches and leaving me sick to my stomach.
When I go to create a custom recording rules the system freezes
up or it crashed my frontend.. and when rebooting, all the 
custom recording rules and scheduled recordings are not showing
but the settings exists.. and then I get an error "mythtv
is using all inputs but there are no active recordings. when attempting
live tv.. this leads me to have to totally pull the plug and leave
the system setting for 5 minutes or so. and if Im lucky it bounces back.
these are just a few of the issues I've encountered..

 Is there a means in Karma to take MythTV back to 0.21 without having
 to reinstall the whole system.? or am I going to have to wipe everything
 out..  where I stand right now.. 0.22 is too unstable and should
 of waited on it until it was stabilized before forcing to down everyones
 throat.. Im wanting to go back until the next LTS version of ubuntu is
 released, because instability every 6 months isnt what I want on a
 media center. I would prefer to set it and forget it once I got it
 working the way I want without it getting messed up very few months.
 If it works dont try and fix it..;)

 One should really be ashamed.. because every release version every 6 months
 should be stable.. doing a side by side comparision of karma to vista
 well.. karma appears full of more bugs, at least where the media center is concerned.
 Out of the 3+ years of using Ubuntu I have been very pleased upto this point..and before
 someone suggests it.. no microcrap isnt an option..

---

### Post by movieman on 2009-11-27
> **t3chn0b0y said:**
> One should really be ashamed.. because every release version every 6 months should be stable..

Only the LTS releases are really considered 'stable', aren't they?

---

### Post by williammanda on 2009-11-28
I'm not one to beat up the free community but this release of ubuntu 9.10 with mythtv isn't a very good representation. I'm considering reverting back to 9.04. The problems I have seen so far are from groups not communicating with each other. Example the screen saver. Also mythtv releasing .22 with storage groups...doesn't work with vob or iso files? This is a pre-release for .23? I have seen too many posts of users confused about what is going on. Get real! I don't care if it is free you don't do that! I agree that this version is very unstable. I can be watching a recorded program and it just quits. Or the adjust fill doesn't keep the adjusted size but reverts back to the original size after skipping forward.
I'm sorry this version mythtv not so much ubuntu has made a step backward on this release.

---

### Post by klc5555 on 2009-11-28
> **t3chn0b0y said:**
> Im having serious issues when editing video, the frames stick.
The same problem happens when fast forward & rewinding.. giving
me serious eye strain, headaches and leaving me sick to my stomach.
When I go to create a custom recording rules the system freezes
up or it crashed my frontend.. and when rebooting, all the 
custom recording rules and scheduled recordings are not showing
but the settings exists.. and then I get an error "mythtv
is using all inputs but there are no active recordings. when attempting
live tv.. this leads me to have to totally pull the plug and leave
the system setting for 5 minutes or so. and if Im lucky it bounces back.
these are just a few of the issues I've encountered..

 Is there a means in Karma to take MythTV back to 0.21 without having
 to reinstall the whole system.? or am I going to have to wipe everything
 out..  where I stand right now.. 0.22 is too unstable and should
 of waited on it until it was stabilized before forcing to down everyones
 throat.. Im wanting to go back until the next LTS version of ubuntu is
 released, because instability every 6 months isnt what I want on a
 media center. I would prefer to set it and forget it once I got it
 working the way I want without it getting messed up very few months.
 If it works dont try and fix it..;)

 One should really be ashamed.. because every release version every 6 months
 should be stable.. doing a side by side comparision of karma to vista
 well.. karma appears full of more bugs, at least where the media center is concerned.
 Out of the 3+ years of using Ubuntu I have been very pleased upto this point..and before
 someone suggests it.. no microcrap isnt an option..

I'd hate to try to do it myself, but ... it is known that the main Jaunty mythtv (0.21) packages run on Ubuntu 9.10.

Accordingly, if after stripping your system down you have ended up with a stable Xubuntu system, you should be able to download the 3 main Jaunty mythtv 0.21 packages (mythtv-common, mythtv-frontend, mythtv-backend) from packages.ubuntu.com, install them (and dependencies) with the gdebi installer, and be on your way to 9.10 plus mythtv 0.21. The 0.21 packages would have to be locked.

But unless there's augmented hardware support in 9.10 you have to have, it must be neater, simpler, and more reliable to blow the system away and do a clean install of 9.04.

---

### Post by tgm4883 on 2009-11-28
> **t3chn0b0y said:**
> Im having serious issues when editing video, the frames stick.
The same problem happens when fast forward & rewinding.. giving
me serious eye strain, headaches and leaving me sick to my stomach.
When I go to create a custom recording rules the system freezes
up or it crashed my frontend.. and when rebooting, all the 
custom recording rules and scheduled recordings are not showing
but the settings exists.. and then I get an error "mythtv
is using all inputs but there are no active recordings. when attempting
live tv.. this leads me to have to totally pull the plug and leave
the system setting for 5 minutes or so. and if Im lucky it bounces back.
these are just a few of the issues I've encountered..

 Is there a means in Karma to take MythTV back to 0.21 without having
 to reinstall the whole system.? or am I going to have to wipe everything
 out..  where I stand right now.. 0.22 is too unstable and should
 of waited on it until it was stabilized before forcing to down everyones
 throat.. Im wanting to go back until the next LTS version of ubuntu is
 released, because instability every 6 months isnt what I want on a
 media center. I would prefer to set it and forget it once I got it
 working the way I want without it getting messed up very few months.
 If it works dont try and fix it..;)

 One should really be ashamed.. because every release version every 6 months
 should be stable.. doing a side by side comparision of karma to vista
 well.. karma appears full of more bugs, at least where the media center is concerned.
 Out of the 3+ years of using Ubuntu I have been very pleased upto this point..and before
 someone suggests it.. **no microcrap isnt an option**..

Why not?

> **williammanda said:**
> I'm not one to beat up the free community but this release of ubuntu 9.10 with mythtv isn't a very good representation. I'm considering reverting back to 9.04. The problems I have seen so far are from groups not communicating with each other. Example the screen saver. Also mythtv releasing .22 with storage groups...doesn't work with vob or iso files? This is a pre-release for .23? I have seen too many posts of users confused about what is going on. Get real! I don't care if it is free you don't do that! I agree that this version is very unstable. I can be watching a recorded program and it just quits. Or the adjust fill doesn't keep the adjusted size but reverts back to the original size after skipping forward.
I'm sorry this version mythtv not so much ubuntu has made a step backward on this release.

**Example the screen saver? **What about the screensaver?

**Also mythtv releasing .22 with storage groups...doesn't work with vob or iso files?**  Yep, I made the change for it. I've seen some user confusion, but not a whole lot. There are posts regarding how to fix it as well.

**This is a pre-release for .23? **Who said that? The pre-release for 0.23 would be running the 0.23 repos on karmic



I really hope that for all the complaints in this thread that bugs have been filed. Heck, there is even a brainstorm section for Mythbuntu that you could put ideas on. And if anyone would like to actually help out I'm sure the Mythbuntu team would welcome the extra developers and could even mentor them in some areas. Speaking from past experience though, neither of you will offer anything helpful to this discussion nor will contact the Mythbuntu team offering help. Instead you will continue to rant here without offering anything constructive. If this is the case, I'll just consider closing this thread.

---

### Post by t3chn0b0y on 2009-11-28
There are also other issues, Im experiencing, the snapshots are blank 1x1 images of the left corner of my desktop.. and when browsing my recordings I have a big brown box in the corner of my screen. I was using the little video playing in the corner instead of snapshots,but that feature, has been removed from 0.22 but the option  to select it is still in the code. which can lead to people "like me" being confused as to how many other features are not in the software that check boxes exist for.[-X .  wondering why its not doing what I set it up to do.   Im curious if the rush to push 0.22 out was because of dependencies being updated that other software packages would of relied on would also be held back.. sacrifice the one for the many..? But I don't want to sit here and cast stones.. I just wish I would of known somehow what I was getting into before I got into it.. and 0.22 does seem as though its nothing but a pre 0.23 release. as I stated earlier about features appearing to be of existence but the code was removed for those features,if say Microsoft would do something like that, they would have alot of explaining to do, I figured what is put on the cd is like buying a copy of windows, its expected to be stable, not experimental,"testing".. but then again what was windows me and vista... LOL...   

I think Im going to pull out my drive, and toss in a empty drive, and do a fresh install.. no upgrade, over upgrade.. and see how many of the problems still exist.. Im not sure if some of them could be caused by the upgrade? and if they still exist I will attempt to take things back..to 0.21 ..  If anyone wants I will post my findings.:popcorn:

---

### Post by t3chn0b0y on 2009-11-28
> **tgm4883 said:**
> 


I really hope that for all the complaints in this thread that bugs have been filed. Heck, there is even a brainstorm section for Mythbuntu that you could put ideas on. And if anyone would like to actually help out I'm sure the Mythbuntu team would welcome the extra developers and could even mentor them in some areas. Speaking from past experience though, neither of you will offer anything helpful to this discussion nor will contact the Mythbuntu team offering help. Instead you will continue to rant here without offering anything constructive. If this is the case, I'll just consider closing this thread.


Where is the brainstorm, and where does one go to get mentoring?
and in so doing one has to have a free system to run unstable software?
I'm already signed up with the mythtv email groups except for trunk..
I dig through the reported bugs everyday. But I find very little information on how one can go about helping in some way. do you know of any good links? and the issues I have,some are reported bugs.

---

### Post by tgm4883 on 2009-11-29
Accessible from any mythbuntu.org website page
[http://mythbuntu.org/gettinginvolved](http://mythbuntu.org/gettinginvolved)

Accessible from any brainstorm page
[http://brainstorm.ubuntu.com/mythbuntu/](http://brainstorm.ubuntu.com/mythbuntu/)

---

### Post by williammanda on 2009-11-29
> **tgm4883 said:**
> **Example the screen saver? **What about the screensaver?

Here are a couple of the posts for the screensaver issue:

[http://ubuntuforums.org/showthread.php?t=1310526]("http://ubuntuforums.org/showthread.php?t=1310526")

[http://ubuntuforums.org/showthread.php?t=1336226]("http://ubuntuforums.org/showthread.php?t=1336226")


> **tgm4883 said:**
> **This is a pre-release for .23? **Who said that? The pre-release for 0.23 would be running the 0.23 repos on karmic

The pre-release statement comes from the wiki:

[http://www.mythtv.org/wiki/MythVideo]("http://www.mythtv.org/wiki/MythVideo")

This is from the wiki:

Storage Groups

Videos in Myth can now be stored on the backend and streamed to the frontend without a NFS or Samba mount. It is critical to note that the Storage Group implementation is not complete, and to take that into consideration when weighing whether to move to MythVideo Storage Groups. Hopefully the transition to Storage Groups will be complete for MythTV .23, **so this should be taken as a technology preview release only**.


> **tgm4883 said:**
> I really hope that for all the complaints in this thread that bugs have been filed. Heck, there is even a brainstorm section for Mythbuntu that you could put ideas on. And if anyone would like to actually help out I'm sure the Mythbuntu team would welcome the extra developers and could even mentor them in some areas. Speaking from past experience though, neither of you will offer anything helpful to this discussion nor will contact the Mythbuntu team offering help. Instead you will continue to rant here without offering anything constructive. If this is the case, I'll just consider closing this thread.

I'm not a software programmer or developer nor do I have any spare equipment to do testing. With that said I do help out regularly sometimes almost daily with replies to other users problems in the mythbuntu forum. I have asked before in the irc room how to help out but I didn't have the above resources. I was unware of any other avenues to help but if I can contribute via the brainstorm section for Mythbuntu, I certainly will.

---

