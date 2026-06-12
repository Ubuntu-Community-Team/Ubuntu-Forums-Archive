---
title: "Call for Ubuntu 10.10 Final ISO Testing"
date: 2010-10-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-10-06
The initial set of candidate images for the final release are now ready, and we're in for one last round of ISO testing for the Maverick cycle.

**[SIZE="3"]What Is ISO Testing?[/SIZE]**

A while before each Ubuntu development milestone release (alphas, betas and the RC), the package archive is frozen, and only bug fixes that help towards a high quality testing release are accepted. During this period, usually on the first day of the week leading to the release, a set of daily images are designated as candidates for release, and are subject to an additional round of testing commonly referred to as "ISO testing", in order to ensure that they're reasonably free of showstopper bugs and ready to be tested by the broader testing audience that grows with each milestone.

**[SIZE="3"]How You Can Help[/SIZE]**

Candidate images for the Ubuntu 10.10 final release are on [the ISO testing tracker]("http://iso.qa.ubuntu.com/"). You can test any number of test cases you'd like, and report bugs. 

We now have [upgrade cases]("http://iso.qa.ubuntu.com/qatracker/build/upgrade/all") to be tested, as well as [some new features]("http://ubuntutesting.wordpress.com/2010/08/03/alpha-3-iso-tracker-new-features/") in the tracker.

If you're unfamiliar with the procedures, there are two good places to start:

[list][*] [Ara Pulido's tutorial]("http://ubuntutesting.wordpress.com/2009/09/21/old-friend-iso-testing-tracker/") on how to use the ISO testing tracker 

[*] The [testing procedures page on the Ubuntu Wiki](https://wiki.ubuntu.com/Testing/ISO/Procedures)[/list]

If you're doing testing for the first time, please read the above, and remember that posting issues here is not enough; you should report your test results in the testing tracker.

If you need immediate help with testing, the best place to go is the #ubuntu-testing [IRC channel]("https://help.ubuntu.com/community/InternetRelayChat") on irc.freenode.net. And feel free to ask any questions you may have on this thread.

---

### Post by kansasnoob on 2010-10-07
I think it looks pretty darn good. I have a few minor concerns with the new ubiquity but they're really the sort of thing that needs to be presented to the design team I suspect.

I've been looking for an "Ubuntu-wiki" regarding the new ubiquity but haven't found anything yet. Sometimes I can go around and around trying to find official documentation.

---

### Post by 23meg on 2010-10-07
> **kansasnoob said:**
> 
I've been looking for an "Ubuntu-wiki" regarding the new ubiquity but haven't found anything yet.

Do you mean a specification? If so:

[https://docs.google.com/View?id=dfkkjjcj_101gnkrpg5v](https://docs.google.com/View?id=dfkkjjcj_101gnkrpg5v)

---

### Post by kansasnoob on 2010-10-07
That is helpful, but I'm actually just being impatient :redface:

I've just been wondering what the 10.10 version of this guide will look like:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Of course you still have to hope that people actually read the documentation but Ubuntu makes it easy enough to find.

But I'm just being impatient. I always get that way the last few days prior to a new release.

I'm particularly curious how they'll write the instructions regarding this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

That screen appears after selecting "Install side by side" and I know what to do, but I fear being offered the "entire disc" and "entire partition" options at the next screen could be very confusing to a first time dual booter.

I suspect that's something that I'll ultimately have to bring up on Ayatana to be considered during Natty design and development. Then again proper documentation may be all that's necessary.

When I'm iso-testing I always try to think, "would I understand this if it were my first Ubuntu experience"? Of course I don't always get it right.

But, considering how long ago the new ubiquity was added, I think the devs did an exemplary job pulling it all together. For sure some people will complain just because it's different. But, aside from that one issue, I think the graphical installer is easy to understand.

I do wish the installer windows could be maximized, but that's just nit-picking.

---

### Post by kansasnoob on 2010-10-07
@ mgunes,

Any idea why there's no upgrade testing yet?

Maybe just pushing out some last minute bug fixes?

---

### Post by teh603 on 2010-10-07
Looks like they are. I saw a bunch of .iso links that were crossed out on the tracker, with the comment "rebuilding" when I visitied it a few seconds ago.

I generally stay out of .iso testing, for what its worth. I don't know enough about the process of building one or anything like that to really be able to contribute much.

---

### Post by 23meg on 2010-10-07
> **kansasnoob said:**
> That is helpful, but I'm actually just being impatient :redface:

I've just been wondering what the 10.10 version of this guide will look like:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)


The page you linked to is part of the community-maintained documentation, so you don't have to wonder; you can go ahead and adapt it to the new Ubiquity yourself if you feel like it.

> **kansasnoob said:**
> @ mgunes,

Any idea why there's no upgrade testing yet?

Maybe just pushing out some last minute bug fixes?

Not sure; I'll ask around. It might be that it's too late to mess with the release upgrader any further.

---

### Post by 23meg on 2010-10-07
> **teh603 said:**
> 
I generally stay out of .iso testing, for what its worth. I don't know enough about the process of building one or anything like that to really be able to contribute much.

You don't have to know how to build an ISO; they're already built for you to test. 

Everything you need to know is in the links in the original post.

---

### Post by sr_guy on 2010-10-07
I ran a mandatory update last night that downloaded and updated about 150 packages. Rebooted in the morning and X is dead, gdm won't start, and even the ssh server that I configured stopped working, so I'm unable to ssh in from work. Has this issue been brought up? I would hate to download the final release, and a fw updates later X and gdm stop working.

---

### Post by kansasnoob on 2010-10-07
Sadly things have gone downhill in my testing :(

I'd considered this bug largely cosmetic:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

But I'd now call it a show-stopper!

With four NTFS partitions I get this:

[ATTACH]171586[/ATTACH]

Not good at all!

The forums will be besieged with complaints of lost Win 7 OS's and data!

Time to brush up on TestDisk & PhotoRec :(

---

### Post by kansasnoob on 2010-10-07
> **mgunes said:**
> The page you linked to is part of the community-maintained documentation, so you don't have to wonder; you can go ahead and adapt it to the new Ubiquity yourself if you feel like it.

I don't have the skills to adapt that to 10.10. I wish I did :)

I do try very hard to troubleshoot casper and ubiquity because what turned me on to Ubuntu initially was how well the Live session and the installer behaved.

I fear we're moving in the wrong direction right now with ubiquity, but I also realize that development is never painless.

---

### Post by ranch hand on 2010-10-07
> **kansasnoob said:**
> Sadly things have gone downhill in my testing :(

I'd considered this bug largely cosmetic:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

But I'd now call it a show-stopper!

With four NTFS partitions I get this:

[ATTACH]171586[/ATTACH]

Not good at all!

The forums will be besieged with complaints of lost Win 7 OS's and data!

Time to brush up on TestDisk & PhotoRec :(
Clear as mud.  Should be simple to understand by the kind of folks Ubuntu appears to be targeting.

I have no intention of looking at the ABT or GH forums after this one.

---

