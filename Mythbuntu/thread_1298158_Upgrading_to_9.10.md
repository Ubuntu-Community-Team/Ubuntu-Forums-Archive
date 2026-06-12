---
title: "Upgrading to 9.10"
date: 2009-10-22
forum: Mythbuntu
---

### Post by cabbage on 2009-10-22
Just a quick question... I've just read the 9.10 RC mythbuntu page and am left wondering how best to upgrade.

I'm on 9.04 running 0.21-fixes.

Am I right in thinking that I must upgrade to 0.22 before I upgrade the OS to 9.10? Or will a dist-upgrade do both at the same time?

As I would like my box to be as stable as possible, I'd prefer to be following the 0.22-fixes branch rather than trunk. How can I do this with mythbuntu?


Cheers,

Cabbage.

---

### Post by luigidk on 2009-10-22
I second this question.

I JUST implemented Mythbuntu 9.04 as a from scratch install.  But MythTV .22 seems like a no-brainer.

Do I upgrade from .21 to .22 with an apt-get upgrade for MythTV and then do an Ubuntu 9.04 to 9.10 upgrade?

Or - would I bet better off for any reason to start w/9.10rc from scratch?  

I'll be implementing my HDHOMERUN this weekend so would love to get to 9.10rc at that time also!

---

### Post by amar on 2009-10-23
I was just about to ask that exact question. Might be worth putting the answer in the release notes. I found the comment about the 0.22 systems confusing. A fuller explanation may be required for those of us who installed jaunty then just let it run.

> It is very important to note that this release is only compatible with MythTV 0.22 systems. Previous Mythbuntu releases can be upgraded to MythTV 0.22 with the builds located at [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

Thanks

---

### Post by lerrup on 2009-10-23
+1 to this question!

---

### Post by bsntech on 2009-10-23
As far as I know, a dist-upgrade from 9.04 to 9.10 will also update to MythTV 0.22rc1.

I just did a standard Ubuntu install and then installed all of the items afterwards.

I did a mysql dump of the mythconverg database and then re-imported after the update.  Myth will then update the schema from the 0.21 MythTV to 0.22 MythTV the first time you run the mythbackend.

---

### Post by tgm4883 on 2009-10-23
Thanks for the heads up.

[http://www.mythbuntu.org/MythTV-compatibility](http://www.mythbuntu.org/MythTV-compatibility)

Let me know if this page needs further clarification.

---

### Post by cabbage on 2009-10-24
Thanks tgm4883 that does help clarify things.

Will there be a 0.22-fixes option in the mythbuntu weekly builds repo soon?

---

### Post by tgm4883 on 2009-10-24
> **cabbage said:**
> Thanks tgm4883 that does help clarify things.

Will there be a 0.22-fixes option in the mythbuntu weekly builds repo soon?

it's already there, which version of mythbuntu-repos are you using?

---

### Post by cabbage on 2009-10-24
2-0ubuntu0+mythbuntu5

---

### Post by tgm4883 on 2009-10-24
Go to the mythbuntu website and download the new package

[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

### Post by luigidk on 2009-10-25
I am on 9.04 - and downloaded mythbuntu-repos.deb.

Then I did a sudo dpkg -i mythbuntu-repos.deb 

I was asked a question (?) - replied no
I was asked another question (?) - replied no

Then I get an error.

When I tried sudo dpkg -i mythbuntu-repos.deb again - I immediately rcvd the error.  

I don't see any changes to mythbuntu control center?

AM I correct in assuming that i use mythbuntu-repos to upgrade from 9.04 .21 to 9.10 .22 ???

---

### Post by cabbage on 2009-10-25
Thanks - I've downloaded it (again) and now I have the choice of which version I want. If I select 0.22 it puts trunk into the sources file.

I guess I just have to wait a bit for the proper 0.22-fixes repo...

---

### Post by tgm4883 on 2009-10-25
> **luigidk said:**
> I am on 9.04 - and downloaded mythbuntu-repos.deb.

Then I did a sudo dpkg -i mythbuntu-repos.deb 

I was asked a question (?) - replied no
I was asked another question (?) - replied no

Then I get an error.

When I tried sudo dpkg -i mythbuntu-repos.deb again - I immediately rcvd the error.  

I don't see any changes to mythbuntu control center?

AM I correct in assuming that i use mythbuntu-repos to upgrade from 9.04 .21 to 9.10 .22 ???

What error message?  No, you don't do use mythbuntu-repos to upgrade to 9.10 0.22, you use it to upgrade from 9.04 0.21 to 9.04 0.22


> **cabbage said:**
> Thanks - I've downloaded it (again) and now I have the choice of which version I want. If I select 0.22 it puts trunk into the sources file.

I guess I just have to wait a bit for the proper 0.22-fixes repo...

*Jedi mind trick* That isn't the info you're looking for. 


Forget what is in the sources file. Look at the packages that are in the 0.22-trunk repo. They are the 0.22-fixes packages. There will be no change in the name of the repos.

0.23 going forward will all just be named the version number.

---

### Post by luigidk on 2009-10-25
THis is the error I get:
(Reading database ... 139201 files and directories currently installed.)
Preparing to replace mythbuntu-repos 5-0ubuntu0+mythbuntu~karmic (using mythbuntu-repos.deb) ...
Unpacking replacement mythbuntu-repos ...
Setting up mythbuntu-repos (5-0ubuntu0+mythbuntu~karmic) ...
OK
OK
[: 92: =: unexpected operator

FOllowup:  I removed the package use synaptics package manager - then redownloaded - reapplied (sudo dpkg -i ...) and then answered YES to the questions.  No errors now (guess answering NO to all questions defeats the purpose)

NOW - how/where do I go to upgrade to .22 (understanding I'll still be at 9.04).  

After I upgrade to .22 - can I do a separate ubuntu upgrade to 9.10 - how?

---

### Post by tgm4883 on 2009-10-25
> **luigidk said:**
> THis is the error I get:
(Reading database ... 139201 files and directories currently installed.)
Preparing to replace mythbuntu-repos 5-0ubuntu0+mythbuntu~karmic (using mythbuntu-repos.deb) ...
Unpacking replacement mythbuntu-repos ...
Setting up mythbuntu-repos (5-0ubuntu0+mythbuntu~karmic) ...
OK
OK
[: 92: =: unexpected operator

FOllowup:  I removed the package use synaptics package manager - then redownloaded - reapplied (sudo dpkg -i ...) and then answered YES to the questions.  No errors now (guess answering NO to all questions defeats the purpose)

NOW - how/where do I go to upgrade to .22 (understanding I'll still be at 9.04).  

After I upgrade to .22 - can I do a separate ubuntu upgrade to 9.10 - how?

Hmm, ok. Thanks for the info.

You don't need to upgrade to 0.22 before you upgrade to 9.10. Just doing the OS upgrade to 9.10 will upgrade mythtv

---

### Post by luigidk on 2009-10-25
I am so sorry for my confusion.

THought the mythbuntu repos was to upgrade 9.04 .21 to 9.04 .22... though I have not figured out how to do that upgrade either - after loading the repos package - I have not seen how to upgrade.

But that sounds moot - if all I need to do is upgrade from 9.04 to 9.10... 

DO I do that with Synaptics?  or ???

---

### Post by neutron68 on 2009-10-25
I'm also trying to update to 9.10 with myth 0.22.

**Ideally, I'd like to have someone lay out a list of necessary steps to accomplish the goal. **

I see it printed that we should upgrade to 9.10 and that will upgrade us to myth 0.22 automatically?
HOW do we upgrade to 9.10 - list of steps, please.

I downloaded the Mythbuntu 9.10 RC cd-rom.  Is this how we upgrade to 9.10?

Clarification appreciated,
Eric

---

### Post by NTolerance on 2009-10-25
> **neutron68 said:**
> I'm also trying to update to 9.10 with myth 0.22.

**Ideally, I'd like to have someone lay out a list of necessary steps to accomplish the goal. **

I see it printed that we should upgrade to 9.10 and that will upgrade us to myth 0.22 automatically?
HOW do we upgrade to 9.10 - list of steps, please.

I downloaded the Mythbuntu 9.10 RC cd-rom.  Is this how we upgrade to 9.10?

Clarification appreciated,
Eric

I'm with you 100%.  I hope that we can hammer out some step-by-step instructions for those looking to make their Mythbuntu 9.04 system a 9.10 system.  Maybe it's just a dist-upgrade, but surely there are some detailed items we should document to help upgraders.

As far as your question about the CD goes, traditionally version upgrades have been handled by the update manager program or apt-get.  I'm not sure if the CD can be used for upgrades; hopefully someone can answer this question.  Here are the commands used to upgrade via the update manager:

```
sudo apt-get update
sudo update-manager -d
```

Probably best not to run those commands yet until we get some answers in this thread regarding the upgrade process. 

Of particular interest to me are changes to Intel video performance, Mythvideo, and Mythweb.  I'd like to know what new default settings will need attention in MythTV 0.22.

Edit:  I'd like to add that we should absolutely clarify which methods are appropriate to different types of upgrades e.g., people who are running stock Mythbuntu 9.04 vs. people who are running Mythbuntu 9.04 with custom repositories for Mythtv packages not available in stock 9.04.

---

### Post by uncle hammy on 2009-10-25
I am going to tag onto this thread, because it seems like the right place.  I am running 9.04 with the JYA Vdpau Repos.  

I downloaded and installed the Automatic Repos as linked earlier in this thread, selected yes to "use weekly builds" and upgrade to "0.22".  

In sources, I disabled the JYA repos.

I backed up my current Db.

I then opened Update Manager and did a "Check", and it came up with a pile of updates....ALL of them for themes only, though.  I ran the updates and tried opening my frontend, and it displayed the background image of my theme (MythCenter-wide) and closed.

Since all the updates were for themes only I thought "Well, I probably have 0.22 themes, with 0.21 components, that's probably the issue", so I went into Synaptic and uninstalled everything MythTV related.  I then did a sudo apt-get update to update my sources.  I then went back into Synaptic and saw that everything MythTV related now said 0.22+fixes, so I went through an manually installed everything.

I opened up my frontend, got 2 warnings that the Db was going to be updated, and let it happen.  As soon as that was done? started?  just the backup got done?, it immediately closed down again.  I tried opening the frontend again, but I was right back to the "see background, close" scenario.

I finally gave up, uninstalled everything MythTV, re-enabled the JYA repos, updated my sources, and reinstalled everything MythTV and restored my Db backup.

Anyone able to shed any light on what I did wrong?  Is it because I was trying to go from the JYA repos to the Mythbuntu Auto Build repos?  Should I have uninstalled everything, and enabled the 0.21 Weekly builds, installed all that, THEN tried to go to 0.22 Weekly?

---

### Post by Al_Vampyre on 2009-10-26
> **uncle hammy said:**
> 
I then opened Update Manager and did a "Check", and it came up with a pile of updates....ALL of them for themes only, though.  

Exactly the same thing happened to me last night (although thankfully I didn't have any subsequent issues). When I enabled 0.22 in the mytbuntu repos all I got were updates for themes, nothing else updated.

---

### Post by neutron68 on 2009-10-26
Hey, tgm4883!  We need you!

You appear to know what we need to do to properly upgrade our systems to 9.10.  
Can you help us by telling us the necessary steps?  

That'd be GREAT!  :)

Eric

---

### Post by tgm4883 on 2009-10-26
I've had a few requests to write a guide on how to do the upgrade to 9.10. The fact that I have gotten these requests means there is some confusion somewhere. I would like to figure out where this confusion is coming from and fix the issue. The upgrade should be simply following the Ubuntu upgrade guide. One of the developers is doing an upgrade from 9.04 to 9.10 in the next 24 hours and noting any oddities that they find, so you may want to wait a bit before upgrading.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by NTolerance on 2009-10-26
> **tgm4883 said:**
> I've had a few requests to write a guide on how to do the upgrade to 9.10. The fact that I have gotten these requests means there is some confusion somewhere. I would like to figure out where this confusion is coming from and fix the issue. The upgrade should be simply following the Ubuntu upgrade guide. One of the developers is doing an upgrade from 9.04 to 9.10 in the next 24 hours and noting any oddities that they find, so you may want to wait a bit before upgrading.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

For me, the confusion stems from two things:

1.  The beta/RC news on the Mythbuntu site regarding 9.10 doesn't have any upgrade notes or instructions.  If it's as simple as the normal Ubuntu dist-upgrade method, that's great, just put it on the Mythbuntu site.  ;)

2.  MythTV is an inherently complex application.  Most users are aware of this and probably keep a keen eye out for MythTV-specific upgrade concerns.

---

### Post by tonycollinet on 2009-10-27
Agreed -  I simply assumed that upgrading mythbuntu would be more complex than a normal Ubuntu upgrade. 

For example I expected a need to separately upgrade Ubuntu and Myth TV.

To avoid the questions - simply state a simple "upgrade as shown here" type link on the mythbuntu homepage.

---

### Post by neutron68 on 2009-10-27
> **tgm4883 said:**
> I've had a few requests to write a guide on how to do the upgrade to 9.10. The fact that I have gotten these requests means there is some confusion somewhere. I would like to figure out where this confusion is coming from and fix the issue. The upgrade should be simply following the Ubuntu upgrade guide. One of the developers is doing an upgrade from 9.04 to 9.10 in the next 24 hours and noting any oddities that they find, so you may want to wait a bit before upgrading.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Reasons for my confustion:

1.  Lack of any kind of instructions for the upgrade.  Since we are upgrading Mythbuntu, there should be a how-to list right on the page [http://www.mythbuntu.org/9.10/rc](http://www.mythbuntu.org/9.10/rc)

2.  There were questions in the thread about using the weekly-repos.deb to upgrade to the mythtv 0.22 files.  This method was discouraged, but no list of preferred steps were presented - confusing!

3.  I looked at the "upgrading" link you referenced.  On that page, it shows a picture of the Update Manager with the message "New distribution release 9.04 is available" (with an UPGRADE button).
My Update Manger does NOT have any notice of "New distribution release 9.10" anywhere - and NO Upgrade button.
Users can't follow the posted documentation, because it isn't correct or up to date.
**I guess that no Upgrade button will show up in the Update Manager until the release candidate 9.10 becomes the final release 9.10?  Is that right?**

I think some specific documentation will go a long way towards clearing up confusion.

Thanks,
Eric

---

### Post by uncle hammy on 2009-10-27
OK, I have managed to get upgrade to 0.22 on 9.04.  I had a pile of issues with the DB upgrade, but finally got it all sorted out.  Only to be greeted by a message.

```

The server uses network protocol version 40, but this client only understands version 50.  Make sure you are running compatible versions of the backend and frontend.

```

Seriously?  I JUST downloaded BOTH from the MythBuntu WeeklyBuild Repo, and they don't have comnpatible versions up there?

I didn't have this problem last night.  Although I couldn't get my Db updated, I WAS able to launch the frontend and mythtv-setup without the "procotol" error...I just couldn't do anything, unless I felt like starting from scratch with my recordings, settings, etc.  Now, I have the Db finally upgraded, and I can't launch the frontend / mythtv-setup!

Here's the kicker.  At various times tonight in my torment, I was able to get into the backend setup WITH a restored Db...but couldn't open the Frontend because of the "protocol" error.  At other times, I couldn't open either because of the "protocol" error.

This is becoming the most convoluted, hair pulling, ridiculous software upgrade I have ever had the misfortune of taking on.

---

### Post by neutron68 on 2009-10-27
> **uncle hammy said:**
> OK, I have managed to get upgrade to 0.22 on 9.04.
How did you do the upgrade?  
- By changing the mythbuntu-repos.deb to use version 0.22?
- Or did the Update Manager have a 9.10 UPGRADE button to press?

Eric

---

### Post by uncle hammy on 2009-10-27
I upgraded MythTV only, not Mythbuntu.  I simply added the 0.22 mythbuntu-repos and ran the update manager.

However, I am currently in the process of putting it all back together to 0.21, because I can't get anything to run with 0.22.

Perhaps this wasn't the best thread to post in.  However, this thread seems to be getting attention, and has become a mix of upgrading to 0.22 on 9.04 and upgrading 9.04 to 9.10.

---

### Post by funkydan2 on 2009-10-27
Hi,

I don't know how much a 'it worked(ish) for me' report for upgrading is helpful, but here it is anyway.

Last night I upgraded from Jaunty->Karmic by running 'sudo do-release-upgrade -d' from the command line (couldn't get the GUI way to work). The upgrade 'sort of' worked perfectly, except right at the end, when it was rebuilding the nVidia modules my / partition ran out of disk space and the upgrade stopped. Foolhardily I pushed on, ran 'sudo aptitude dist-upgrade' and the install finished and removed the unneeded packages. (Not recommended to anyone - it probably won't work for you.)


Rebooting the computer worked (went out of the room, so I couldn't see what was happening with Xsplash). However I wasn't automatically logged into xfce. But I logged in, and MythTV 0.22 started up right away. I was alerted to a few database upgrades (which I consented to) and next thing I knew I was in the MythTV frontend and could see all me old recordings and watch live TV.

Quite the frontend, and used the Mythbuntu Control centre to setup automatic login, enable medibuntu & install relevant packages, downloaded the latest mythbuntu repositories deb and setup the 0.22-fixes source.

A few little problems.
- LiveTV was a bit unstable, so I rescanned my channels in mythtv-setup. Seems to be working properly now.
- I was hit by a [bug in mythtv-status]("https://bugs.launchpad.net/ubuntu/+source/mythtv-status/+bug/437803"). The bug report says that it was fixed in Karmic Alpha 6, but the version of mythtv-status hasn't changed since intrepid.
- There was also permission problems relating to the new way that MythVideo gets cover art. Resulted in getting error emails from the Cronjob. Needed to make a few directories, reset permissions, and change the MythVideo settings to point to these directories.

Everything else seems to be going ok.

---

### Post by shocksafe on 2009-10-28
Upgrading myself now

Check here - [http://www.ubuntu.com/getubuntu/releasenotes/910overview](http://www.ubuntu.com/getubuntu/releasenotes/910overview)

It is advised your install is up to date.

I updated all then enabled the "pre-released updates" in update manager-> settings (not sure if this is needed but didn't get the upgrade button until I did this).
Then closed and reopened update manager and the upgrade button was there.

Upgrading now, see how it goes :)

---

### Post by mrand on 2009-10-28
> **funkydan2 said:**
> - I was hit by a [bug in mythtv-status]("https://bugs.launchpad.net/ubuntu/+source/mythtv-status/+bug/437803"). The bug report says that it was fixed in Karmic Alpha 6, but the version of mythtv-status hasn't changed since intrepid.I don't see where it said it was resolved in Alpha 6.  Unfortunately maintainers [did not]("http://packages.ubuntu.com/search?searchon=names&keywords=mythtv-status+") have time to get the fixed version of mythtv-status pulled in from debian and updated in time for the official 9.10 release.

There are two slightly related tickets open on this:
[https://bugs.launchpad.net/mythtv-status/+bug/455542](https://bugs.launchpad.net/mythtv-status/+bug/455542) (to get updated mythtv-status)
[https://bugs.launchpad.net/ubuntu/+source/mythtv-status/+bug/243205](https://bugs.launchpad.net/ubuntu/+source/mythtv-status/+bug/243205) (to minimize the difference between debian and ubuntu versions of mythtv-status)

> - There was also permission problems relating to the new way that MythVideo gets cover art. Resulted in getting error emails from the Cronjob. Needed to make a few directories, reset permissions, and change the MythVideo settings to point to these directories. Interesting.  Could you be a bit more specific about what changes were needed?  It might help other, less experienced users.

Thanks to you (and everyone else) for being understanding while the Mythbuntu team tries to keep up with the very rapid pace of changes regarding Mythtv and all the surrounding applications.

[INDENT]Marc[/INDENT]

---

### Post by blackoper on 2009-10-28
I upgraded from 9.04 yesterday. I just went into terminal and typed: sudo update-manager -d

After doing the upgrade, on reboot nvidia drivers were messed up (kind of expected). I had to ssh in from another box and then I updated to the newest nvidia .run package off their website. Everything else seems to be working fine. (I was already using the .22 auto builds)

---

### Post by neutron68 on 2009-10-28
> **blackoper said:**
> I upgraded from 9.04 yesterday. I just went into terminal and typed: sudo update-manager -d


Is the command line interface absolutely necessary to initiate the upgrade, or can this upgrade be done ENTIRELY through the Update Manager GUI?  
Is there a check box that needs to be checked so the Update Manager will recognize distribution updates (such as 9.10)?

You see, I've got some friends who I support that are newbie Linux users, at best.  I end up walking them through all command line operations, via a phone call.  Ideally, I'd like for them to see an "UPGRADE TO 9.10" button in their update manager.

Eric

---

### Post by jmore9 on 2009-10-28
use ALT + F2

then enter in the box that shows up

update-manager -d

and accept the recommended actions as they come up.

---

### Post by tgm4883 on 2009-10-28
IIRC, It should just be available via the update manager gui after release.

---

### Post by neutron68 on 2009-10-28
> **tgm4883 said:**
> IIRC, It should just be available via the update manager gui after release.
Good to know!

I can certainly live with the command line activation of the update, during this pre-release period.

Thanks!
Eric

edit 9:55pm Central Daylight Time

The command-line upgrade process does work.  I have crossed over the mountain top and see the land of myth 0.22.  It seems to work for the most part. :)
There are some minor oddities, but it mostly works.

---

### Post by NTolerance on 2009-10-28
> **neutron68 said:**
> Is the command line interface absolutely necessary to initiate the upgrade, or can this upgrade be done ENTIRELY through the Update Manager GUI?  
Is there a check box that needs to be checked so the Update Manager will recognize distribution updates (such as 9.10)?

You see, I've got some friends who I support that are newbie Linux users, at best.  I end up walking them through all command line operations, via a phone call.  Ideally, I'd like for them to see an "UPGRADE TO 9.10" button in their update manager.

Eric

Here's a screenshot for fun and profit:

---

### Post by tgm4883 on 2009-10-28
> **neutron68 said:**
> Good to know!

I can certainly live with the command line activation of the update, during this pre-release period.

Thanks!
Eric

edit 9:55pm Central Daylight Time

The command-line upgrade process does work.  I have crossed over the mountain top and see the land of myth 0.22.  It seems to work for the most part. :)
There are some minor oddities, but it mostly works.

It's good to know what those oddities are and what trouble people are running into. I'm creating a FAQ for just this type of thing at [http://www.mythbuntu.org/FAQ](http://www.mythbuntu.org/FAQ)

---

### Post by neutron68 on 2009-10-28
> **tgm4883 said:**
> It's good to know what those oddities are and what trouble people are running into. I'm creating a FAQ for just this type of thing at [http://www.mythbuntu.org/FAQ](http://www.mythbuntu.org/FAQ)
Gotcha.  I started a new thread to report a couple of the oddities I noticed.  Mostly everything works, though. :)

Eric

---

### Post by funkydan2 on 2009-10-29
> **mrand said:**
> I don't see where it said it was resolved in Alpha 6.  Unfortunately maintainers [did not]("http://packages.ubuntu.com/search?searchon=names&keywords=mythtv-status+") have time to get the fixed version of mythtv-status pulled in from debian and updated in time for the official 9.10 release.
[/Quote
My bad. Sorry, I misread the first comment on that bug report.
 Interesting.  Could you be a bit more specific about what changes were needed?  It might help other, less experienced users.

[[QUOTE=mrand;8181852]
Thanks to you (and everyone else) for being understanding while the Mythbuntu team tries to keep up with the very rapid pace of changes regarding Mythtv and all the surrounding applications.

Well, my directory structure is a little different from how MythBuntu sets things up by default (partly so that I can keep all my media on a large LVM and partly a hang-up from starting with KnoppMyth a few years back).

What I had to do was make a bunch of directories, for me in the /myth/video directory, change their group to mythtv and change their permissions to 775.
So the commands would be
mkdir banners fanart posters screenshots trailers
chgrp myttv banners fanart posters screenshots trailers
chmod 775 banners fanart posters screenshots trailers

However, having done that I still have a problem with the mythvideo cron job that runs ever hour:
> 
run-parts: /etc/cron.hourly/mythvideo exited with return code 1

Though having read some of the transition guide, could these problems be occurring because I haven't set up storage groups?

Daniel

---

### Post by neutron68 on 2009-10-29
I just noted the new links to upgrade documentation on the Mythbuntu 9.10 announcement sub-page.  That's helpful!  

Thank you to all responsible for their efforts in laying out the needed steps for upgrade! :D

Eric

---

### Post by tonycollinet on 2009-10-30
Seconded - thanks.

---

### Post by NTolerance on 2009-10-30
My upgrade won't happen until next week, but I'm still reading and hoping to learn all I can about the process.  I was checking out the 9.10 release notes and it appears that if you upgrade via the GUI you'll get MySQL 5.1, but if you upgrade via the terminal you'll stay with MySQL 5.0.

[http://www.ubuntu.com/getubuntu/releasenotes/910#MySQL%20upgrade](http://www.ubuntu.com/getubuntu/releasenotes/910#MySQL%20upgrade)

---

### Post by sk8er3810 on 2009-10-30
I'm running Mythbuntu 9.04.
I backed up my system including mysql databases.  I tried do the "Network Upgrade".  However this failed due to at the current time of this post the packages server was down. (Just checked the status and it looks like its grabbing the updates now)

I had torrented all of the ISOs so I have the alternate disk.  I followed the "Alternate CD" upgrade instructions however the gui window did not pop up.  So I ran via the command line  "sh /cdrom/cdromupgrade".  

Really looking forward to some of the features of both 9.10 and .22 like faster boot times, Storage Groups

I'm running the update on my primary backend/frontend and depending on how it goes I will do the upgrade on my second frontend.

---

### Post by KnisterPeter on 2009-11-06
```
run-parts: /etc/cron.hourly/mythvideo exited with return code 1 			 		
```

I also have this problem and its very annoying to receive this every hour. Any update on this? I do not want to just disable this script.

---

### Post by KnisterPeter on 2009-11-06
And now after upgrading to .22-fixes I get error messages like this:
```

! Warning: Download IOError on URL for Filename(*/home/markusw/*.mythtv/MythVideo/Fanart/Terminator_fanart.jpg)
Orginal URL([http://images.thetvdb.com/banners/fanart/original/80344-21.jpg](http://images.thetvdb.com/banners/fanart/original/80344-21.jpg))
IOError urllib.quote URL([http://images.thetvdb.com/banners/fanart/original/80344-21.jpg](http://images.thetvdb.com/banners/fanart/original/80344-21.jpg))

```

This is output from the jamu.py script running hourly.
When I changes images.thetvdb.com to [www.thetvdb.com](www.thetvdb.com) it does work.

---

### Post by liquidox on 2009-11-06
Same problem here. The script is using images.thetvdb.com which is down. It is supposed to use thetvdb.com which provides load balancing.

---

### Post by liquidox on 2009-11-06
> **liquidox said:**
> Same problem here. The script is using images.thetvdb.com which is down. It is supposed to use thetvdb.com which provides load balancing.
Hmm, been fiddling with it all morning, and seem to have fixed it now, just not sure how. Try doing a full clean of the DB by making the Jamu janitor not find any files, then do the normal run again from the start.

---

### Post by Freddan101 on 2009-11-07
I tried to export the Recordings info from my current 0.21-fixes system (which is running Mythbuntu 8.10) and import it into my new clean Mythbuntu 9.10 system using these commands:

mysqldump -u root -p -t mythconverg record recorded oldrecorded recordedprogram recordedrating recordedmarkup recordedseek > recordings.sql

mysql -u root -pmythtv mythconverg -p < recordings.sql

Though, all special characters (Swedish å, ä ö) get messed up and replaced by other characters and I also get an error message "ERROR 1062 (23000) at line 74: Duplicate entry '1001-2009-03-04 19:59:00-0-0' for key 'PRIMARY'".

Should I do this some other way? Maybe upgrade my current system to 0.22 first before exporting the database?

---

### Post by Freddan101 on 2009-11-11
> **Freddan101 said:**
> I tried to export the Recordings info from my current 0.21-fixes system (which is running Mythbuntu 8.10) and import it into my new clean Mythbuntu 9.10 system using these commands:

mysqldump -u root -p -t mythconverg record recorded oldrecorded recordedprogram recordedrating recordedmarkup recordedseek > recordings.sql

mysql -u root -pmythtv mythconverg -p < recordings.sql

Though, all special characters (Swedish å, ä ö) get messed up and replaced by other characters and I also get an error message "ERROR 1062 (23000) at line 74: Duplicate entry '1001-2009-03-04 19:59:00-0-0' for key 'PRIMARY'".

Should I do this some other way? Maybe upgrade my current system to 0.22 first before exporting the database?I ended up upgrading from 0.21 to 0.22 on my current system which worked like a charm. I can highly recommend doing it this way before upgrading the OS itself.

---

### Post by korgman on 2009-11-11
The upgrade went mostly flawless.  I had to reset auto login at boot.  And alsamixer muted my HDMI output but all pretty easy to fix.  The biggest problem I have is that the C+ profile I was using is having a hard time coming out of FWD and RWD. I get 
"2009-11-11 20:58:15.131 NVP(9): prebuffering pause"
and then it bumps me back to the menu.

VDPAU works fine with REW and FWD but its having choppy playback on two HD stations when watching live TV or prerecorded show.  So, either profile has problems.

---

### Post by SiHa on 2009-11-12
> **korgman said:**
>  ... alsamixer muted my HDMI output but all pretty easy to fix. 

Care to tell me how?

I have HDMI Audio in Myth and VLC after selecting the right alsa source. 

But I cannot for the life of me get HDMI audio in anything else, and it seems that it's because alsamixer & the xfce mixer aren't aware of it.

TIA,

Simon

---

### Post by novellahub on 2009-11-12
> **SiHa said:**
> Care to tell me how?

I have HDMI Audio in Myth and VLC after selecting the right alsa source. 

But I cannot for the life of me get HDMI audio in anything else, and it seems that it's because alsamixer & the xfce mixer aren't aware of it.

TIA,

Simon

Simon -

Try this in your asound.conf file:

```

  pcm.!default {
     type plug
     slave.pcm "hdmi"
  }

```


Here is what my file looks like:
```

   pcm.!default {
       type hw
       card 0
       device 3
   }
   pcm.!default {
      type plug
      slave.pcm "hdmi"
   }

```

The slave.pcm "hdmi" was key for me to get sound outside of Mythtv (Hulu Desktop as a example).

---

### Post by SiHa on 2009-11-12
Aagh!
Did that and got no sound at all. Opened the mixer from the multimedia menu, and got 'Gstreamer can't find any sound devices'. At the time, my wife was sitting next to me tapping her fingers and tutting because I'd stopped TV just to 'Try something quick'.
Renamed the file so it won't be used for now, got the mixer back, and got my Myth sound at least.
I'll have play around when I have a bit of time at the weekend.
Thanks for the pointers though, I think I'm getting somewhere because I at least managed to change something...

Edit: Fixed (Thanks larsolav)
Added
```
defaults.pcm.device 3
```
To /etc/asound.conf and changed MythTV sound to Alsa:default. Now I have audio in all apps it seems.

Happy Bunny.

---

