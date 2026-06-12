---
title: "Maverick should introduce a system to provide *optional* upgrades to common programs"
date: 2010-05-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by MCVenom on 2010-05-09
And to that effect, I've filed a bug under the One Hundred Paper Cuts project here: [https://bugs.launchpad.net/hundredpapercuts/+bug/578045](https://bugs.launchpad.net/hundredpapercuts/+bug/578045) Alright, it was stupid of me to file this as a papercut :P

It's rather long, so I'll summarize it here: It's easier to get the newest versions of many popular FOSS applications on proprietary operating systems than on Ubuntu, because those projects may not provide deb packages for the software.* To reduce the amount of surfing around and/or installing debs from untrusted sources, as well as potentially unstable PPAs I am proposing that the option to upgrade to the newest stable version of programs be added to the Ubuntu Software Center.* That way an easy and safe way to install the newest version of a program like Firefox can be offered to the user, under the condition that the upgraded version might not receive bug fixes and other forms of support. I believe such a feature would also be vital to the mainstream acceptance of Ubuntu and bring us ever closer to solving Bug #1. 

What do you all think? I'm eager to hear criticism and ideas on how to make the proposal better (or why it shouldn't be implemented at all). :D

PS: This article, posted around the time of the Firefox 3.6 launch sums up my concerns pretty well:
[B][Installing Firefox 3.6: One more reason Linux isn't  ready for the  prime-time mass market ]("http://blogs.computerworld.com/15443/talling_firefox_3_6_one_more_reason_linux_isnt_ready_for_the_prime_time_mass_market");)

[/B]>  Upgrading on a Windows machine is simplicity itself.  Download a  file, run it, follow the prompts, and you're done. On the  Mac it's even  easier; download the file, do a drag operation, and  you're done. And  that's just if you want to get the upgrade right away.  At some point,  Firefox will essentially do the upgrade itself. 
  How about on Linux --- specifically Unbuntu, the version most people   see as the one best suited for mass use? Good luck, unless you are very   familiar with the innards of the operating system. Looking to upgrade, I   downloaded the proper file, then unpacked it. At that point, though,   all I saw was a folder structure filled with files, and no install file,   no hint, no advice on what to do next. 


---

### Post by Ibidem on 2010-05-09
Absolutely--but it strikes me, that it could be done via an optional "<release>-latest" repository.

It was really annoying using Abiword 2.4 when 2.6.8 was out (Dapper), and it is annoying have only Firefox 3.0 (on a Jaunty install) when 3.5-3.7 fix several security risks and run faster.

---

### Post by Ellipsis on 2010-05-09
Something of this kind is really needed. I have seen many complaints about Ubuntu not offering the latest version of a particular program easily. 

This only causes problems in the long run with people installing from unstable sources or with major "noob-barriers".

---

### Post by zekopeko on 2010-05-09
And the never-ending timed releases vs rolling releases debate rages on...

I find it funny that you filed such a huge request as a paper-cut.

---

### Post by Starks on 2010-05-09
I like how you gave this topic numerous tags to make it look legitimate.

---

### Post by MCVenom on 2010-05-09
> **Starks said:**
> I like how you gave this topic numerous tags to make it look legitimate.
I... don't see the point you're trying to make, sorry.

---

### Post by MCVenom on 2010-05-09
> **zekopeko said:**
> And the never-ending timed releases vs rolling releases debate rages on...

I find it funny that you filed such a huge request as a paper-cut.
It's not a 'rolling release'. That'd be like calling Windows a rolling release OS. :p

You may have a point on the second thing, though. :|

---

### Post by MCVenom on 2010-05-09
If you voted no, the question remains -- why shouldn't users be able to upgrade their programs as easily as they would on Windows?

---

### Post by Merk42 on 2010-05-09
I think something to help that is in effect for Firefox.

I'm guessing 3.7 wouldn't be offered when it comes out, but when 3.6 is EOL since that's less work for the devs.

---

### Post by arpanaut on 2010-05-09
Nice Idea...

But who do you expect to give the time to collect, package, maintain, ensure security updates, etc?

Like the developers don't have enough on their plates re: development of new releases and maintenance of what is already provided. 

(BTW all that comes to you free of cost)

---

### Post by Ellipsis on 2010-05-09
Although I love the Ubuntu release cycle and generally stick with the preinstalled software and versions, I like many others sometimes do need a more uptodate version of certain programs.

---

### Post by MCVenom on 2010-05-09
> **arpanaut said:**
> Nice Idea...

But who do you expect to give the time to collect, package, maintain, ensure security updates, etc?

Like the developers don't have enough on their plates re: development of new releases and maintenance of what is already provided. 

(BTW all that comes to you free of cost)
Doesn't need to be 'maintained', not even by MOTUs; simply packaged and uploaded. What I'm suggesting is a rather skeletal idea, simply to have the software available without hassle so far.

The bug has been marked invalid (to be honest, I wasn't sure what would happen with it. Puzzling out 'the right channels' to make suggestions to devs isn't always easy). I suspect I will find a different, better suited venue to suggest it to the devs later. In the meantime, I would really like feedback and ideas on getting it into a more coherent, convincing argument; I really believe this should be implemented somehow. I'll look over the SoftwareCenter Roadmap as suggested (I can't believe I didn't think to give that a read through) and see what's there that's like or could be like what I'm thinking of. In the meantime, let's keep the discussion going!

---

### Post by ranch hand on 2010-05-09
> **arpanaut said:**
> Nice Idea...

But who do you expect to give the time to collect, package, maintain, ensure security updates, etc?

Like the developers don't have enough on their plates re: development of new releases and maintenance of what is already provided. 

(BTW all that comes to you free of cost)
Perfectly stated.

The point seems to be that these outside devs are not supplying debs.  Therefore Ubuntu ought to.

Which ignores the fact that FF, for instance, has very clear instructions for installing its packages on any platform.

Also that Ubuntu and other Linux distros has the tools for installing this kind of thing available.

Just how lazy are we getting here when we start expecting a free OS to do all the work for us?  Good grief, who is expected just to catalog all the FOSS apps out there, let alone create debs for them.

---

### Post by lykwydchykyn on 2010-05-09
Well, in theory we have a system.  It's called the backports repository.  In theory, if you subscribe to the backports repository you'll get new releases of software backported to the current stable release.

*in theory*

In practice, I don't know what the point of the backports repository is.  It's used for so little it seems almost pointless.

Have a look at the complete listing of backports for Karmic:

[http://packages.ubuntu.com/karmic-backports/allpackages](http://packages.ubuntu.com/karmic-backports/allpackages)

If you exclude all the packages for the point release of KDE (note that it is a point release, not the major release of KDE that came out in the same time frame), there's little if anything of significance remaining.  Check the same list for Jaunty, the situation is the same.

So other than providing minor bugfix releases of KDE (why wouldn't that go in ubuntu-updates, since it's just a bugfix?), backports does next to nothing.  Why not actually backport important applications?  Why leave people to subscribe to half a dozen PPA's to get the latest upstream versions compiled when that's precisely what a backports repository is supposed to be?

To sum it up: we don't need another system.  We need the one we already have to be made useful.

---

### Post by arpanaut on 2010-05-09
> **ranch hand said:**
> Perfectly stated.

The point seems to be that these outside devs are not supplying debs.  Therefore Ubuntu ought to.

Which ignores the fact that FF, for instance, has very clear instructions for installing its packages on any platform.

Also that Ubuntu and other Linux distros has the tools for installing this kind of thing available.

Just how lazy are we getting here when we start expecting a free OS to do all the work for us?  Good grief, who is expected just to catalog all the FOSS apps out there, let alone create debs for them.

**Thank You!**

---

### Post by ronacc on 2010-05-09
one thing that ubuntu could do to help is to stop using custom names for some of their libs , which causes generic debs and other installers to barf with dependancy problems where none really exist .

---

### Post by autocrosser on 2010-05-09
> **lykwydchykyn said:**
> Well, in theory we have a system.  It's called the backports repository.  In theory, if you subscribe to the backports repository you'll get new releases of software backported to the current stable release.

*in theory*

In practice, I don't know what the point of the backports repository is.  It's used for so little it seems almost pointless.

Have a look at the complete listing of backports for Karmic:

[http://packages.ubuntu.com/karmic-backports/allpackages](http://packages.ubuntu.com/karmic-backports/allpackages)

If you exclude all the packages for the point release of KDE (note that it is a point release, not the major release of KDE that came out in the same time frame), there's little if anything of significance remaining.  Check the same list for Jaunty, the situation is the same.

So other than providing minor bugfix releases of KDE (why wouldn't that go in ubuntu-updates, since it's just a bugfix?), backports does next to nothing.  Why not actually backport important applications?  Why leave people to subscribe to half a dozen PPA's to get the latest upstream versions compiled when that's precisely what a backports repository is supposed to be?

To sum it up: we don't need another system.  We need the one we already have to be made useful.

You must remember the proposed repo also---between it & backports you get a fair amount of updated material---Plus, to those that really want the newest & greatest---between being HERE & a bit of looking 'round you can get most anything that is available.

No distro has the resources for what you ask for zero money---it takes manpower & time to keep things going.....all for no cost to you.

---

### Post by 23meg on 2010-05-10
> **autocrosser said:**
> You must remember the proposed repo also---between it & backports you get a fair amount of updated material---Plus, to those that really want the newest & greatest---between being HERE & a bit of looking 'round you can get most anything that is available.

-proposed only has to do with [testing and verification]("https://wiki.ubuntu.com/QATeam/PerformingSRUVerification") of [stable release updates]("https://wiki.ubuntu.com/StableReleaseUpdates"). It's not intended for new upstream versions.

---

### Post by 23meg on 2010-05-10
> **BlackOtaku said:**
> I'll look over the SoftwareCenter Roadmap as suggested (I can't believe I didn't think to give that a read through) and see what's there that's like or could be like what I'm thinking of.

The "trust level ratings" goal is meant to provide the infrastructure for exactly what you're looking for.

---

### Post by lykwydchykyn on 2010-05-10
> **autocrosser said:**
> You must remember the proposed repo also---between it & backports you get a fair amount of updated material---Plus, to those that really want the newest & greatest---between being HERE & a bit of looking 'round you can get most anything that is available.


Check this page for more details on the difference between backports, proposed, updates, etc:

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

If you read the description of backports, it sounds like the perfect place for new upstream releases.
> 
No distro has the resources for what you ask for zero money---it takes manpower & time to keep things going.....all for no cost to you.

Sure.  Everyone gets this, I think.  I'm not demanding a thing.

But what I find interesting is that in most cases all the work is already being done, but just not getting to the right places.  We don't need every possible app backported just for the heck of it.  But when a new firefox comes out, there are at least 3 or 4 PPA duplicating effort to bring it to people (off the top of my head, there's ubuntuzilla, ricotz,and moz-daily PPA).  It's worth asking the question, why, with so many willing and able to do the work, is this not getting to where it seemingly belongs? (i.e., backports)

My guess is that there are less than 10 applications which, if they were kept current in backports, would silence 90% of the complaining about installing new app versions.

---

### Post by lean on 2010-05-10
The big problem is quality and assurance. When Mozilla creates a new release of Firefox, it has been tested that it works in all distributions, since a lot of people are using nightlies, betaes and so forth.

It should be noted that the release from Mozilla have a different skin than that of Ubuntu - and maybe other changes. But that is just one part of the problem.
The other part is that a lot of programs depends on firefox, or its rendering enginge. If you replace that engine, then you really have to test alle programs that depend on that.


If a backported version of Firefox should be created, it would require a lot of man power to create and test the ubuntu specific features. This is why it is not happening.

But there have been official PPA's with high profile versions of programs. OpenOffice comes to mind, which had a backport for an important OO release.

On the issues of multiple PPA's that are all creating new releases. How do you know it is duplicate effort? Why would people do that?
My guess is there are small differences in the PPA's, or different versions. Also, they are probably copying each others files, so only a small fraction is duplicate work.

Also, you cannot expect people that create PPAs to be good at maintaining a backport releases.

*They cannot be relied on to keep creating new version
*They cannot be expected to cooporate (that is the idea with an ppa, its personal)


An in all, it is a really hard problem to create back ports that have good QA. The easiest solution is just to upgrade every 6 month and be happy about that ;)

---

### Post by MCVenom on 2010-05-10
> **ranch hand said:**
> Perfectly stated.

The point seems to be that these outside devs are not supplying debs.  Therefore Ubuntu ought to.

Which ignores the fact that FF, for instance, has very clear instructions for installing its packages on any platform.

Also that Ubuntu and other Linux distros has the tools for installing this kind of thing available.

Just how lazy are we getting here when we start expecting a free OS to do all the work for us?  Good grief, who is expected just to catalog all the FOSS apps out there, let alone create debs for them.
Well if it takes money to make this a viable *mainstream* OS, then by all means do it. I'm not saying that resources aren't tight, I'm stating that this needs to be implemented regardless. Surely in a way that doesn't provide too many headaches, but still. Personally I'd love it if the upstream would package for us without issue. And when I tried to install FF, there were little to no instructions to be found; there's an old tech blog post (ComputerWorld?) complaining of the issues I described in the installation of it.

Ignoring the basic expectations of modern OSes is why Linux only had a 1% market share in the past. At this rate we'll never see Bug #1 fixed, unless Ubuntu is able to find the ways and means to catch up in what few areas its lacking. The 'It's free, so shut up' argument doesn't work against a culture that's already inclined to believe free = crap. It simply doesn't work when you have the goals Ubuntu has (as defined by Shuttleworth, no one else).

---

### Post by MCVenom on 2010-05-10
> **lykwydchykyn said:**
> If you read the description of backports, it sounds like the perfect place for new But what I find interesting is that in most cases all the work is already being done, but just not getting to the right places.  We don't need every possible app backported just for the heck of it.  But when a new firefox comes out, there are at least 3 or 4 PPA duplicating effort to bring it to people (off the top of my head, there's ubuntuzilla, ricotz,and moz-daily PPA).  It's worth asking the question, why, with so many willing and able to do the work, is this not getting to where it seemingly belongs? (i.e., backports)

My guess is that there are less than 10 applications which, if they were kept current in backports, would silence 90% of the complaining about installing new app versions.

My point exactly. I even made the point that if nothing else, just put a nice, shiny button to link to Getdeb; its better than what we have now. I'd like to see backports used more.

---

### Post by Gourgi on 2010-05-10
> **zekopeko said:**
> i find it funny that you filed such a huge request as a paper-cut.
+1

@BlackOtaku :  your idea is good,i'm all in all with you at this as long as people understand their going to use ***unsupported*** software... **but** filling it as papercut doesn't make sense.
> "A paper cut is a trivially fixable usability bug that the average user would encounter in default installation of Ubuntu or Kubuntu Desktop Edition."

---

### Post by lykwydchykyn on 2010-05-10
> **lean said:**
> 
An in all, it is a really hard problem to create back ports that have good QA. The easiest solution is just to upgrade every 6 month and be happy about that ;)

I'd respond individually, but it's Monday morning and I haven't had enough coffee in me yet.

I just want to point out that (a) backports is not officially supported, so QA is not as big an issue, and (b) most of the time there isn't much to doing a backport.  Something comes into Lucid, you grab the debianized source and run dpkg-buildpackage on it.  If it doesn't have the dependencies, eh, no backport for you.  If it compiles, yay.

Yeah, I'm sure there's a lack of manpower to do this.  Too bad.  Six months isn't a terribly long time to wait, but people want this, and it could be provided.  It's just shame, that's all.

---

### Post by Merk42 on 2010-05-10
*Hypothetical* Latest version of program $Foo is not available for user's current Microsoft OS (Windows XP)
OMG MIKKKRO$OFT THEY JUST WANT TO MAKE YOU UPGRADE FOR $$$$$$$$$

*Hypothetical* Latest version of program $Foo is not available for user's current Canonical OS (Ubuntu 10.04)
It's not possible to do QA and you can't complain because it's FREEEEE

---

### Post by xebian on 2010-05-10
Another clueless idea.  You should 'demand' the devs of your fav apps to build an Ubuntu package :P.  Or much better provide a direct repo link like wine or virtualbox and some others do.

Getting source/compile it/package it/test it/upload to repo is a 'Maintenance' and is not limited to fixing bugs.

---

### Post by autocrosser on 2010-05-10
> **23meg said:**
> -proposed only has to do with [testing and verification]("https://wiki.ubuntu.com/QATeam/PerformingSRUVerification") of [stable release updates]("https://wiki.ubuntu.com/StableReleaseUpdates"). It's not intended for new upstream versions.


Thank you my friend---my bad....I must remember to verify before late-night posting:)

---

### Post by taavikko on 2010-05-10
I voted no.

If severe CVE is found and fixed upstream, it will be delivered by maverick-security.

If someone just wants to have the newest and shiniest software
cause it's da thing....
Use rolling releases... 
Or after official release, upgrade to the next dev release.

ATM we have a good balance with new and shiny and stability.

---

### Post by MCVenom on 2010-05-10
> **taavikko said:**
> I voted no.

If severe CVE is found and fixed upstream, it will be delivered by maverick-security.

If someone just wants to have the newest and shiniest software
cause it's da thing....
Use rolling releases... 
Or after official release, upgrade to the next dev release.

ATM we have a good balance with new and shiny and stability.
Is Windows 7 a rolling release? Is it an unstable development release? Sometimes you have to be like what you're trying to beat. :p

---

### Post by ranch hand on 2010-05-10
The best way to "beat" MS is to not be like them.  Just do a good job of what we do and let MS implode under teh weight of its own bloat and over blown hype.

Emulating crap will end up being crap.

---

### Post by Merk42 on 2010-05-10
> **ranch hand said:**
> The best way to "beat" MS is to not be like them.  Just do a good job of what we do and let MS implode under teh weight of its own bloat and over blown hype.

Emulating crap will end up being crap.

What does that have to do with the topic of the thread?

That sort of comment also rings "be different for the sake of being different" which I would think you of all people would be against.

---

### Post by taavikko on 2010-05-10
> **BlackOtaku said:**
> Is Windows 7 a rolling release? Is it an unstable development release? Sometimes you have to be like what you're trying to beat. :p

When windows has repositories for centralized package handling, it shouldn't be taken as something to aspire to.
(yeah yeah, windows update... only handles few components)

Ubuntu delivers something working OOTB (Windows doesn't)

Somebody already stated that backports is a system to provide *optional* upgrades.

---

### Post by crjackson on 2010-05-10
> **23meg said:**
> -proposed only has to do with [testing and verification]("https://wiki.ubuntu.com/QATeam/PerformingSRUVerification") of [stable release updates]("https://wiki.ubuntu.com/StableReleaseUpdates"). It's not intended for new upstream versions.

Not to mention it can easily bork a stable production machine.  If you're not actually testing, I'd stay away from proposed.

---

### Post by ubername on 2010-05-10
I'm not convinced that adding this functionality would be helpful to the solution to bug #1. In my experience the thing mainstream computer users want is stability. Adding an option, even with conspicuous caveats, to allow easier installation of software which has not been fully tested within the Ubuntu package as a whole, could result in problems which the end user attributes to Ubuntu even though they know they have installed unsupported software.

There are already plenty of ways for the enthusiasts of the latest releases (myself included - I'm on Maverick here!) to get their adrenalin fixes by trying the bleeding edge stuff, and the fact that it might be a little more difficult than simply clicking a button is in my opinion an advantage - it makes you aware that you are venturing beyond the bounds of the 'normal' usage of the OS/package combination which has been released and therefore a little more forgiving when things don't go to plan.

But that said I am sure that if this resource were available you would find many grateful early-adopters. I just don't think that they would represent the community which a solution to bug #1 would target.

---

### Post by Merk42 on 2010-05-10
> **ubername said:**
> I'm not convinced that adding this functionality would be helpful to the solution to bug #1. In my experience the thing mainstream computer users want is stability

If mainstream users just want stability and Windows is the most mainstream OS, then I guess it's also the most stable.

---

### Post by Ibidem on 2010-05-10
The thing is, Ubuntu does have situations where a bug is "fixed in release x.y", but Ubuntu is stuck on an older version--Abiword before Jaunty, for example.
In these cases, stability can only be obtained by using the updated version.

---

### Post by nanog on 2010-05-11
I think the issue here is not whether ubuntu devs/memebers should spend their time repackaging every new mozilla point release but rather the unecessary barrier to installing standard mozilla or open office packages for the inexperienced user. If you run osx or windows installing the very latests mozilla or Oo.o is a one click install. Why do we make it so hard in ubuntu? 

 I also think ubuntu has grown large enough that developers at mozilla and Oo.o should dedicate some resources to making their binaries match ubuntu's look and feel.

---

### Post by MCVenom on 2010-05-11
> **nanog said:**
> I think the issue here is not whether ubuntu devs/memebers should spend their time repackaging every new mozilla point release but rather the unecessary barrier to installing standard mozilla or open office packages for the inexperienced user. If you run osx or windows installing the very latests mozilla or Oo.o is a one click install. Why do we make it so hard in ubuntu? 

 I also think ubuntu has grown large enough that developers at mozilla and Oo.o should dedicate some resources to making their binaries match ubuntu's look and feel.
Been doing some deeper thinking about the issue, and you are absolutely right; we as a community should put more pressure on the upstream. I think Ubuntu and derivatives' growing userbase is enough to justify OS-specific packaging like Windows and Mac have.

---

### Post by kansasnoob on 2010-05-11
I said NO! That's what ppa's are for.

---

### Post by ronacc on 2010-05-11
> **Merk42 said:**
> *Hypothetical* Latest version of program $Foo is not available for user's current Microsoft OS (Windows XP)
OMG MIKKKRO$OFT THEY JUST WANT TO MAKE YOU UPGRADE FOR $$$$$$$$$

*Hypothetical* Latest version of program $Foo is not available for user's current Canonical OS (Ubuntu 10.04)
It's not possible to do QA and you can't complain because it's FREEEEE

there is one vast difference here , in *Hypothetical* #2 you have the tools and source available so you can build the "latest version " yourself if you want it .

---

### Post by 23meg on 2010-05-11
There's a spec to be discussed at UDS that covers a process through which individual developers are to be able to submit applications for deployment on the latest stable release, and users will be able to install them via Software Center:

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-maverick-opportunistic-apps-stable-release](https://blueprints.launchpad.net/ubuntu/+spec/desktop-maverick-opportunistic-apps-stable-release)

---

### Post by kansasnoob on 2010-05-11
> **23meg said:**
> There's a spec to be discussed at UDS that covers a process through which individual developers are to be able to submit applications for deployment on the latest stable release, and users will be able to install them via Software Center:

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-maverick-opportunistic-apps-stable-release](https://blueprints.launchpad.net/ubuntu/+spec/desktop-maverick-opportunistic-apps-stable-release)

I can smell the breakage now :oops:

---

### Post by MCVenom on 2010-05-11
> **kansasnoob said:**
> I said NO! That's what ppa's are for.
PPAs can add unneeded complexity to a system, and many are for development releases of software as opposed to the stable version your average Windows/Mac user would want.

On another note, I know, I'm bringing up Windows a lot; I've been waiting for someone this entire thread to say 'Linux is not Windows!'. I don't think that Ubuntu should emulate Windows, after all there are reasons I don't use it. ;) I just think that ease of install for new programs is still easier in Windows, and is something that if it were improved, users would appreciate it. Also, I see it as a completely optional feature; so it wouldn't cause any issues for those who want to stay with the 'official distribution repositories'. 

I realize it's easier to say 'Well why would users want to have the newest versions of a particular package?" "Why must it be made any easier?" or "We don't have the resources right now", but the first two questions would be missing the point I'm trying to make, which is that there will be those who will benefit, and those who don't use the feature. No one would be forcing you to use the upgrades, but they'd be there in a more trusted and easy to obtain form if you did want to use it. 

The third is something that requires some thought, as to what resources do we need to fulfill this idea, and if it's worth spending those resources, and what's the best way to implement this if it is worth spending, so that we don't spend more than we need to. This is what I hope comes out of a discussion on this topic; that somehow I can convince a few people that this is a good idea to make things easier for inexperienced users, and we can continue to have a discussion on how to best implement this. I'm glad to see dialogs on making getting *after repo freeze* software easier have been going on among the devs, shows me that I'm not the first one that thought of this and give me hope we'll see something in the future. :D

---

### Post by MCVenom on 2010-05-11
> **23meg said:**
> There's a spec to be discussed at UDS that covers a process through which individual developers are to be able to submit applications for deployment on the latest stable release, and users will be able to install them via Software Center:

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-maverick-opportunistic-apps-stable-release](https://blueprints.launchpad.net/ubuntu/+spec/desktop-maverick-opportunistic-apps-stable-release)
I think this is a great idea. :D

---

### Post by Merk42 on 2010-05-12
> **ronacc said:**
> there is one vast difference here , in *Hypothetical* #2 you have the tools and source available so you can build the "latest version " yourself if you want it .

Considering I used the same program, $Foo, in both examples, it's not a difference at all.

While users could "just build the latest version", the point is users shouldn't have to.

Hopefully to some extent the spec that 23meg may address that

---

### Post by nanog on 2010-05-12
The experienced user can run the latest stable Oo.o or mozilla simply by running a single shell command. And I am not talking about dev builds but stable releases that work well in ubuntu. I think more pressure should be applied on upstream to release proper packages instead of tarballs (mozilla) and fragmented binaries (oracle).

---

### Post by psusi on 2010-05-12
As has already been pointed out, that is what the -backports repo is for.  The problem is, who wants to spend their time backporting the latest release of a package to an old release of Ubuntu?  Just run the latest release of Ubuntu instead.

Even deciding if a package should be backported is difficult.  Is it a significant enough improvement that people WANT it backported?  Is it stable and tested enough that it isn't likely to cause breakage?  These questions are not easy to answer and those who are in a position to do so are probably better off spending their time getting the latest version into the development release, testing it, and fixing bugs.

---

### Post by screaminj3sus on 2010-05-12
Absolutely, the biggest problem I have with ubuntu is a couple months in to a release its packages already start becoming outdated, you either have to add ppas or hunt for debs. (and hope there are ppas/debs for the apps you want to update)

---

### Post by powder on 2010-05-12
This idea is probably not feasible considering conflicting dependencies, circular dependencies, and not to mention a lot of work and headache for maintainers.  Also, in my opinion six months is not a long time to wait for upgrades.

---

### Post by lykwydchykyn on 2010-05-12
> **psusi said:**
> As has already been pointed out, that is what the -backports repo is for.  The problem is, who wants to spend their time backporting the latest release of a package to an old release of Ubuntu?  Just run the latest release of Ubuntu instead.

I think the idea is that people want backports for the *current stable* Ubuntu.  This happens every release cycle.  Firefox and OpenOffice, to name two, generally release a new versions about halfway through the Ubuntu development cycle.  People want to install these.

Then of course there's LTS.  A person may not need or want the newest kernel, GNOME, or libwhatsit, but they may need the newest OpenOffice, or want the newest version of some game.
> 
Even deciding if a package should be backported is difficult.  Is it a significant enough improvement that people WANT it backported?  Is it stable and tested enough that it isn't likely to cause breakage?  These questions are not easy to answer and those who are in a position to do so are probably better off spending their time getting the latest version into the development release, testing it, and fixing bugs.

I don't understand why we are shooting down a system that already exists.  Apparently there is a reason why the Ubuntu devs created -backports and haven't dumped it yet.  Apparently they feel it is feasible to provide new upstream releases to the current stable Ubuntu, limitations notwithstanding.

The question is, why isn't it used more and kept up to date more than it is?  We can speculate on the answer, but I'd be interested to hear from someone involved in development.

---

### Post by powder on 2010-05-12
> **lykwydchykyn said:**
> The question is, why isn't it used more and kept up to date more than it is?  We can speculate on the answer, but I'd be interested to hear from someone involved in development.

I'm not a developer, but after reading the Backports wiki we can conclude:

1. Users must file bug reports in order to request a backport and the request must meet all of the requirements laid out for a backport

2. Some packages can't or won't be backported for whatever reason

---

### Post by lykwydchykyn on 2010-05-12
> **powder said:**
> I'm not a developer, but after reading the Backports wiki we can conclude:

1. Users must file bug reports in order to request a backport and the request must meet all of the requirements laid out for a backport

2. Some packages can't or won't be backported for whatever reason

Right, I'd arrived there on my own.  The question is, which things are *actually preventing* the full use of backports?

Maybe it's just that nobody is submitting backport requests.  Maybe the requests can't be met because of dependency or other technical issues.  Maybe there aren't enough active developers on the backports team.

Who knows?

---

### Post by screaminj3sus on 2010-05-12
> **powder said:**
> This idea is probably not feasible considering conflicting dependencies, circular dependencies, and not to mention a lot of work and headache for maintainers.  Also, in my opinion six months is not a long time to wait for upgrades.

Depends, I remember one older version of ubuntu included this crap beta version of gaim, and shortly after release pidgin came out and was far improved and they refused to update it. this was before the days of ppa's though and they really make this issue more or less not a problem for most. I remember I used to hate older versions of ubutnu because Firefox was always so outdated.

---

### Post by seeker5528 on 2010-05-12
> **lykwydchykyn said:**
> Well, in theory we have a system.  It's called the backports repository.  In theory, if you subscribe to the backports repository you'll get new releases of software backported to the current stable release.

I think many of the back ports that are available are through PPAs, and that probably makes more sense, since the backports repository is all or nothing unless you modify configurations by hand and PPAs allow adding an individual repository for a specifc package or group of packages.

> **ronacc said:**
> one thing that ubuntu could do to help is to stop using custom names for some of their libs , which causes generic debs and other installers to barf with dependancy problems where none really exist .

If these things are barfing, then how generic are they really?

If they actually wanted them to be generic, then they should be compiled in an LSB compliant way, even if they will be provided as .deb instead of blah-blah.lsb-version.architecture.rpm.

Later, Seeker

---

### Post by krazyd on 2010-05-12
I didn't read the entire 6 pages of this thread, but I voted no for a couple of reasons.

**0. We already have a solution**

PPAs, backports repository.

**1. Lack of People Power.**

Ubuntu developers are very busy as it is. They are always working hard on the next release - building a new operating system every 6 months and making it work well is a monumental task already. These people don't want to be creating and testing packages for every new version of every piece of software out there on two different software stacks at the same time.

**2. *Lack of People Power* (it's worth repeating because it is so fundamental)**

There is already an awesome build system which canonical makes available for free (launchpad PPAs) and which anyone is free to use. Many people do and there are many PPA's which track the latest versions of popular packages (xorg-edgers, kubuntu-beta, rvm's mplayer & smplayer, rekonq-daily are the ones I use).

If your pet package isn't available, then it's very simple to do a bit of reading and upload some new packages to your own PPA. Chances are that if there isn't already a PPA with your package available, then it's just not that popular, so surely it's not worth Ubuntu devs time to maintain.

**3. Support.**

Tracking and fixing bugs is hard enough with people running the different ubuntu releases. Doing the same thing with dozens of different versions of the same package would be a nightmare and there just aren't enough people triaging bugs as it is (see points 1 & 2).

------------

**So in summary:** We already have PPAs for this purpose. If you want a new package which isn't in a PPA, then it simply can't be that popular: create a PPA *yourself* and upload to it - it's not that hard. and Ubuntu developers have got better things to do (like making the next release awesome!). **Become an active member of the Free Software community!** :)

---

### Post by ccw on 2010-05-13
Ubuntu cannot be all things for all people. Its time based release has been a key policy since its beginnings ( [https://lists.ubuntu.com/archives/ubuntu-announce/2004-October/000003.html](https://lists.ubuntu.com/archives/ubuntu-announce/2004-October/000003.html) )

I'm not saying it right or wrong. Its Ubuntu.

There are plently of linux distributions out there. distrowatch.com is a good place to start. Fedora if I recall right has a looser update policy. There's also Gentoo. Or grab from Debian Sid or even Ubuntu development branch (currently Maverick).

Or start your own distro. Linux is great that way.

---

### Post by eyelessfade on 2010-05-13
> **krazyd said:**
> 

I agree with you. If you want a newer version make a ppa, or find one.
Many software projects already have ppas. wine, virtualbox or xbmc.

---

### Post by eyelessfade on 2010-05-13
stupid, my browser timed out...

---

### Post by cariboo on 2010-05-13
This whole discussion is moot, as the average user, normally only uses the software that comes installed when they purchase the system. We are **not average users**, we know how to install newer versions of software that we use, and the ppa's make it even easier. Remember Ubuntu is aimed at the first time user, who is a lot more average than we are.

---

### Post by snowpine on 2010-05-13
Just what Ubuntu needs, an easy way to make it less stable. :(

---

### Post by Merk42 on 2010-05-13
> **snowpine said:**
> Just what Ubuntu needs, an easy way to make it less stable. :(

If a newer version of an unrelated program can bring down the entire OS that seems like a flaw of Linux in general

---

### Post by exploder on 2010-05-13
> Just what Ubuntu needs, an easy way to make it less stable. 

PCLinuxOS manages to provide application updates with no breakage and they have 1/10th the number of people Canonical has. GetDeb provides application updates without breakage for Ubuntu, so there is no stability issues being caused by application updates. 

I would be ashamed to state that upgrading applications could cause stability issues, that would be like admitting that the system was poorly built in the first place wouldn't it?

---

### Post by Longinus00 on 2010-05-14
> **exploder said:**
> 
I would be ashamed to state that upgrading applications could cause stability issues, that would be like admitting that the system was poorly built in the first place wouldn't it?

No, it admits the upgraded application might have bugs.

---

### Post by Speed_arg on 2010-05-14
> **Longinus00 said:**
> No, it admits the upgraded application might have bugs.

Or fix bugs.

---

### Post by exploder on 2010-05-14
> Or fix bugs.

That's how I see it.

---

### Post by krazyd on 2010-05-14
> **exploder said:**
> That's how I see it.

Well if there's a bug in your favourite package, make a PPA for it or compile it yourself - it's not that hard.

If there are no updated packages already (in the official repos or in a PPA) then obviously the package just isn't that popular (or the bug specific to you). 

In that case, I'd much rather ubuntu developers' time was spent improving the next release for *everyone* rather than helping an *individual* who [s]is too lazy[/s] doesn't have time to help themselves.

I think ubuntu already does a pretty good job of backporting fixes in important packages.

---

### Post by Merk42 on 2010-05-14
> **krazyd said:**
> Well if there's a bug in your favourite package, make a PPA for it or compile it yourself - it's not that hard.

If there are no updated packages already (in the official repos or in a PPA) then obviously the package just isn't that popular (or the bug specific to you). 

In that case, I'd much rather ubuntu developers' time was spent improving the next release for *everyone* rather than helping an *individual* who [s]is too lazy[/s] doesn't have time to help themselves.

I think ubuntu already does a pretty good job of backporting fixes in important packages.

Would you at least agree that PPAs need to more discoverable?

---

### Post by krazyd on 2010-05-15
> **Merk42 said:**
> Would you at least agree that PPAs need to more discoverable?

Perhaps.

But if you are capable of finding out that a bug has been fixed upstream (presumably by checking out the upstream forum/mailing-list/bug-tracker), then you are capable of finding an upstream PPA.

People shouldn't be adding PPA's just for the sake of having something newer as there are potentially new bugs introduced upstream. Ubuntu can't possibly (and shouldn't) track PPA bugs.

I think the current system is a useful filter; if you don't know what a PPA is or how to find one, then you shouldn't be using one.

---

### Post by flipper9 on 2010-05-15
Ubuntu Tweak makes it easy to add PPA repositories for updated software on Ubuntu.  Why not use that instead of trying to get Ubuntu to change how their system works?

---

### Post by screaminj3sus on 2010-05-15
> **snowpine said:**
> Just what Ubuntu needs, an easy way to make it less stable. :(

I hate the mentality among linux users that newer always = less stable. Newer packages usually include bugfixes and such... Newer can just as easily be MORE stable as less stable.

New != Unstable.

---

### Post by ranch hand on 2010-05-15
> **screaminj3sus said:**
> I hate the mentality among linux users that newer always = less stable. Newer packages usually include bugfixes and such... Newer can just as easily be MORE stable as less stable.

New != Unstable.
snowpine was not referring to new as a problem.  He was referring to not getting all the packages that should go with what you are trying to install and use.

The reference was particularly speaking of new folks that do not know enough to investigate the process fully.  Those are the folks that this change in default is aimed at.

I am having a little trouble with what the problem here is.  I change the preferences in synaptic first off on any install.  I would think that most folks that have been around a while do too.

It needs done and it is the easy way to set up apt.

---

### Post by snowpine on 2010-05-15
> **screaminj3sus said:**
> I hate the mentality among linux users that newer always = less stable. Newer packages usually include bugfixes and such... Newer can just as easily be MORE stable as less stable.

New != Unstable.

I have no problem with newer packages (I'm typing this from Debian Unstable). But I am a big fan of either time based release (all packages are frozen at the release date, and receive only bug fixes and security patches), or rolling release (everything is constantly updated to the latest stable version). 

I do not like mixing the two models. You end up with a mix of old and new applications that were not tested or intended to coexist. I don't often worry about individual applications making my system unstable; I worry about unintended interactions between applications that were never tested to work together. 

That is the great thing about Ubuntu's current release model; everyone using Ubuntu 10.04 is using version 2.01 of Application X, version 3.31 of Application Y, and version 1.6 of Application Z. Everything is tested to work together as a stable whole.

---

### Post by ronacc on 2010-05-15
> **snowpine said:**
> I have no problem with newer packages (I'm typing this from Debian Unstable). But I am a big fan of either time based release (all packages are frozen at the release date, and receive only bug fixes and security patches), or rolling release (everything is constantly updated to the latest stable version). 

I do not like mixing the two models. You end up with a mix of old and new applications that were not tested or intended to coexist. I don't often worry about individual applications making my system unstable; I worry about unintended interactions between applications that were never tested to work together. 

That is the great thing about Ubuntu's current release model; everyone using Ubuntu 10.04 is using version 2.01 of Application X, version 3.31 of Application Y, and version 1.6 of Application Z. Everything is tested to work together as a stable whole.

in the original question did you notice the word "optional" ?  I take that to mean that you would have to deliberately select the newer packages . If you are so worried about stability stick with the normal updates and refrain from installing the "lateset and greatest " .

---

### Post by snowpine on 2010-05-15
> **ronacc said:**
> in the original question did you notice the word "optional" ?  I take that to mean that you would have to deliberately select the newer packages . If you are so worried about stability stick with the normal updates and refrain from installing the "lateset and greatest " .

Then I'm afraid I don't understand the original suggestion. All Linux users have the "option" to install the latest Firefox from [firefox.com]("http://firefox.com"), the latest OpenOffice from [openoffice.org]("http://openoffice.org"), or the latest VirtualBox from [virtualbox.org]("http://virtualbox.org"). (Not to mention the various PPAs, .deb downloads, and backports repositories available to Ubuntu users.) If you want the freshest apples, you go to the apple orchard and pick them straight from the tree. 

Ubuntu is like a big truck that drives to all the farms, gathers the best fruits and vegetables, packages them together, and delivers them to your house twice a year. You don't get the freshest ingredients, but you get a well-balanced meal delivered to your door, for free, with minimal effort on your part. It is what it is. :)

---

### Post by MCVenom on 2010-05-17
> **snowpine said:**
> Then I'm afraid I don't understand the original suggestion. All Linux users have the "option" to install the latest Firefox from [firefox.com]("http://firefox.com"), the latest OpenOffice from [openoffice.org]("http://openoffice.org"), or the latest VirtualBox from [virtualbox.org]("http://virtualbox.org"). (Not to mention the various PPAs, .deb downloads, and backports repositories available to Ubuntu users.) If you want the freshest apples, you go to the apple orchard and pick them straight from the tree. 

Ubuntu is like a big truck that drives to all the farms, gathers the best fruits and vegetables, packages them together, and delivers them to your house twice a year. You don't get the freshest ingredients, but you get a well-balanced meal delivered to your door, for free, with minimal effort on your part. It is what it is. :)
Firefox doesn't offer a *.deb, and many *new* users won't know what to do with some random *.tar.bz2. You would. I would. I didn't a few months ago ^^;

---

### Post by xebian on 2010-05-17
> **BlackOtaku said:**
> Firefox doesn't offer a *.deb, and many *new* users won't know what to do with some random *.tar.bz2. You would. I would. I didn't a few months ago ^^;

That's why those who can't just wait until Uncle Ubuntu delivery comes around.  In addition to the bi-annual delivery it also makes emergency/security delivery.  

Firefox updates are pretty much current in Ubuntu. So what's your point?

---

### Post by MCVenom on 2010-05-17
> **xebian said:**
> That's why those who can't just wait until Uncle Ubuntu delivery comes around.  In addition to the bi-annual delivery it also makes emergency/security delivery.  

Firefox updates are pretty much current in Ubuntu. So what's your point?
That a Windows user won't want to wait, and we'll hear about it in the form of a thousand annoying threads from confused new users if Ubuntu starts to get more mainstream ;)

Just spare us the inevitably misplaced threads asking "What do I do with a tarball?", "What's a PPA? Can I trust it?", "I was told not to download software outside the repos, will this give me viruses?" preemptively, make it easier for those who want it. Trusted PPAs in USC, and an 'always-open' repo between releases are great steps forward.

---

### Post by MCVenom on 2010-05-17
This article, posted around the Firefox 3.6 launch epitomizes why I believe this is important. It is titled, 
[B][Installing Firefox 3.6: One more reason Linux isn't ready for the  prime-time mass market ]("http://blogs.computerworld.com/15443/talling_firefox_3_6_one_more_reason_linux_isnt_ready_for_the_prime_time_mass_market");)

[/B]>  Upgrading on a Windows machine is simplicity itself. Download a  file, run it, follow the prompts, and you're done. On the Mac it's even  easier; download the file, do a drag operation, and you're done. And  that's just if you want to get the upgrade right away. At some point,  Firefox will essentially do the upgrade itself. 
  How about on Linux --- specifically Unbuntu, the version most people  see as the one best suited for mass use? Good luck, unless you are very  familiar with the innards of the operating system. Looking to upgrade, I  downloaded the proper file, then unpacked it. At that point, though,  all I saw was a folder structure filled with files, and no install file,  no hint, no advice on what to do next. 


---

### Post by jetsam on 2010-05-17
Linux: Not safe for tech bloggers.

---

### Post by MCVenom on 2010-05-17
> **jetsam said:**
> Linux: Not safe for tech bloggers.
If a tech blogger on a popular IT site thinks that it's too difficult, even if he can't spell Ubuntu, I thinks that's a sign something's wrong ;)

---

### Post by nanog on 2010-05-17
Those who talk about stability are missing the point. If you install STABLE firefox, chrome, GIMP,  or Open office they tend to JUST WORK. Why are stable updates that are immediately available to anyone running Windows or OSX not made equally available to Linux users? Its time for linux and Ubuntu to actively discourage the antiquated tarball release mechanism. 
(I think this is also an argument for Ubuntu to work more closely with Debian to make sure we do not stray too far from our roots.)

---

### Post by jetsam on 2010-05-17
Yes, I agree we should compromise our carefully honed distribution network for the sake of Pansy McWilliams at LiveBlog.HotNews.MicrosoftNot.Net.COM

/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/
Look ma! A picket fence!  Think I can hit a home run from the back yard?

---

### Post by MCVenom on 2010-05-17
> **nanog said:**
> Those who talk about stability are missing the point. If you install STABLE firefox, chrome, GIMP,  or Open office they tend to JUST WORK. Why are stable updates that are immediately available to anyone running Windows or OSX not made equally available to Linux users? Its time for linux and Ubuntu to actively discourage the antiquated tarball release mechanism. 
(I think this is also an argument for Ubuntu to work more closely with Debian to make sure we do not stray too far from our roots.)
All great points that I wholeheartedly agree with. :)

---

### Post by xebian on 2010-05-17
> **BlackOtaku said:**
> This article, posted around the Firefox 3.6 launch epitomizes why I believe this is important. It is titled, 
[B][Installing Firefox 3.6: One more reason Linux isn't ready for the  prime-time mass market ]("http://blogs.computerworld.com/15443/talling_firefox_3_6_one_more_reason_linux_isnt_ready_for_the_prime_time_mass_market");)

[/B]

It's because Firefox arrogance not to release debs file/and rpms.  And they don't even release a 64-bit.

One more reason to not use Firefox.  Instead use those who release debs file - Opera, Google Chrome.

---

### Post by MCVenom on 2010-05-17
> **xebian said:**
> It's because Firefox arrogance not to release debs file/and rpms.  And they don't even release a 64-bit.

One more reason to not use Firefox.  Instead use those who release debs file - Opera, Google Chrome.
Great point, the whole 'It's not our job to package for you' attitude is a big part of this problem. But it is, for better or worse the second most widely used browser, and one a new Linux user is likely to use or be used to. :P

---

### Post by xebian on 2010-05-17
> **nanog said:**
> Those who talk about stability are missing the point. If you install STABLE firefox, chrome, GIMP,  or Open office they tend to JUST WORK. Why are stable updates that are immediately available to anyone running Windows or OSX not made equally available to Linux users? Its time for linux and Ubuntu to actively discourage the antiquated tarball release mechanism. 
(I think this is also an argument for Ubuntu to work more closely with Debian to make sure we do not stray too far from our roots.)

It's because Firefox bias to Windows/OSX.  They should release debs files 32/64-bit just like Opera, Google Chrome, OO, Virtualbox, others.  

If not then something like a binary executable that install itself.

I think you guys are barking at the wrong tree.

---

### Post by MCVenom on 2010-05-17
> **xebian said:**
> It's because Firefox bias to Windows/OSX.  They should release debs files 32/64-bit just like Opera, Google Chrome, OO, Virtualbox, others.  

If not then something like a binary executable that install itself.

I think you guys are barking at the wrong tree.
Firefox isn't the only one though, for example, Filezilla doesn't package for deb/rpm. I'm sure there are others as well that don't. Part of it can be made easier on our end, but it's become increasingly clear that we need to pressure those projects that don't make *.debs but make Windows/OSX installers into making Ubuntu-ready, easy-to-install packages for their programs.

---

### Post by flipper9 on 2010-05-17
> **BlackOtaku said:**
> Firefox doesn't offer a *.deb, and many *new* users won't know what to do with some random *.tar.bz2. You would. I would. I didn't a few months ago ^^;
That's why some of us install "Ubuntu Tweak" which turns all of that work into an easy-to-use GUI, allowing you to add PPAs from an easy to use list, install applications that aren't easily available elsewhere.  Looks like someone has already done this for those who want to be more of a "power user", and go with the latest stuff.

---

### Post by Merk42 on 2010-05-17
> **jetsam said:**
> Yes, I agree we should compromise our carefully honed distribution network for the sake of Pansy McWilliams at LiveBlog.HotNews.MicrosoftNot.Net.COM

/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/
Look ma! A picket fence!  Think I can hit a home run from the back yard?

I seriously think if there was a parallel universe where Microsoft made it difficult to upgrade IE, you'd be quick to blame "MIKKKRO$OFT" for making it difficult and not the users for not bothering to do it.

---

### Post by ranch hand on 2010-05-17
> **Merk42 said:**
> I seriously think if there was a parallel universe where Microsoft made it difficult to upgrade IE, you'd be quick to blame "MIKKKRO$OFT" for making it difficult and not the users for not bothering to do it.
I, personally, would consider that a service to the user.

---

### Post by tgm4883 on 2010-05-17
I voted No. We have PPA's and -backports for this. (And yes, I read the 10 pages.

---

### Post by MCVenom on 2010-05-17
> **tgm4883 said:**
> I voted No. We have PPA's and -backports for this. (And yes, I read the 10 pages.
Backports aren't used for some god forsaken reason and users need to know where the PPAs they want are at and how to install from them easily. Trusted PPAs in the USC is a good step forward, it's safe, trusted, and easy.

---

### Post by snowpine on 2010-05-17
> **nanog said:**
> Those who talk about stability are missing the point. If you install STABLE firefox, chrome, GIMP,  or Open office they tend to JUST WORK. Why are stable updates that are immediately available to anyone running Windows or OSX not made equally available to Linux users? Its time for linux and Ubuntu to actively discourage the antiquated tarball release mechanism. 
(I think this is also an argument for Ubuntu to work more closely with Debian to make sure we do not stray too far from our roots.)

I'm not a Mac user (so I can't speak for OSX), but the last time I ran Microsoft Windows Update, it did **not** update my Firefox, GIMP, Chrome or OpenOffice to the latest versions either.

Having a stable, trusted repository of software with a centralized package manager to handle installing and updating application is my favorite thing about Linux. Canonical says "We won't just support the core OS, we'll also support all of the applications that we bundle with it, with bug fixes and security patches for up to 3 years." They are not forcing you to use their default version, of course, but they are providing you with a stable and supported default.

---

### Post by ronacc on 2010-05-17
no one is proposing forcing these updates on anyone , but it would be a service to those who wish to have the latest FF or GIMP or OO . For myself I do not need canonical to hold my hand , I am quite comfortable with building from source where necessary but that is not what Ubuntu is about . To drag through 2 or 3 release cycles with badly out of date packages is annoying to many .

---

### Post by tgm4883 on 2010-05-17
> **BlackOtaku said:**
> Backports aren't used for some god forsaken reason and users need to know where the PPAs they want are at and how to install from them easily. Trusted PPAs in the USC is a good step forward, it's safe, trusted, and easy.

Define trusted PPA

---

### Post by snowpine on 2010-05-18
> **ronacc said:**
> For myself I do not need canonical to hold my hand , I am quite comfortable with building from source where necessary but that is not what Ubuntu is about . 

Ubuntu is about: "a new... release every 6 months. That means you'll always have the latest and greatest applications that the open source world has to offer." (source: [http://www.ubuntu.com/products/whatisubuntu]("http://www.ubuntu.com/products/whatisubuntu"))

> **ronacc said:**
> To drag through 2 or 3 release cycles with badly out of date packages is annoying to many .

Define "badly out of date." If you stay current with the Ubuntu Update Manager, your applications will be up-to-date with bug fixes and security patches, and from 0 to 6 months behind on the latest features. Canonical apparently considers 0-6 months "the latest and greatest" (your mileage may vary).

If you habitually lagging "2 or 3 release cycles" behind, Canonical assumes either 1) you do not want the latest applications; or 2) you are comfortable updating the applications you need by other means.

(ps On a side tangent, I would counter the "Ubuntu must target the casual Windows user, who demands the latest apps" argument by pointing out that roughly a quarter of Internet Explorer users are using IE7, released 2006, and another quarter are still using IE6, released 2001--only 50% have upgraded to the March 2009 release of IE8!)

---

### Post by Merk42 on 2010-05-18
> **snowpine said:**
> (ps On a side tangent, I would counter the "Ubuntu must target the casual Windows user, who demands the latest apps" argument by pointing out that roughly a quarter of Internet Explorer users are using IE7, released 2006, and another quarter are still using IE6, released 2001--only 50% have upgraded to the March 2009 release of IE8!)

A lot of those are people in a corporate environment who have no control over what version of IE they use. Many companies deliberately stay on IE6 because they're too cheap to pay to get their intranet apps that were written during the dot com bubble rewritten for modern browsers

---

### Post by tgm4883 on 2010-05-18
> **Merk42 said:**
> A lot of those are people in a corporate environment who have no control over what version of IE they use. Many companies deliberately stay on IE6 because they're too cheap to pay to get their intranet apps that were written during the dot com bubble rewritten for modern browsers

Proof?

---

### Post by phrostbyte on 2010-05-18
I definately agreee with the idea. I've been saying it forever, Ubuntu needs better backports. Especially things like Firefox, to expect people to use an outdated Firefox for 4+ months is absurd.

---

### Post by Merk42 on 2010-05-18
> **tgm4883 said:**
> Proof?

Okay here's [two](http://about.digg.com/blog/much-ado-about-ie6) [articles](http://www.itbusinessedge.com/cm/blogs/mah/like-it-or-not-internet-explorer-6-lives-on-in-corporate-it/?cs=40871) I got from a quick search. I'm sure if you found any large company and contacted their IT chances are it'd be the same.

---

### Post by jetsam on 2010-05-18
```
#include stdio.h
                       *
```
> This is my backyard.```
#!/usr/bin/thatwouldbetelling
#There's no spec!  
#So I'm just goofing around.  
#I was gonna pretend it's python but go for J.
                                      
#This is my sandbox

      

                            

#Have you seen my [Hacky Sack?]("http://en.wikipedia.org/wiki/Hacky_Sack")  I lost it.

```

---

### Post by Sophont on 2010-05-18
There is an unavoidable conflict between being almost cutting edge up-to-date and being well-tested and stable.

All distros (all OS actually) have their own compromise between those extremes.

Ubuntu compromise  a 6-month cycle. That means your favourite could be 0-6 months out of date - on average 3 months.

Big deal.

Sure, there are times when I would have liked a more up-to-date package with a particular feature/bug fix I'm looking for - but OTOH packaging and testing involves effort (or if you cut the effort you get bad quality). But getting them a couple months later is not a horrible fate.

And most users will never notice. It's only a small percentage of us geeks who would notice (or even care) that some cool new feature is available upstream.

If always being up-to-date is so important and you are geek enough to even know about it then why not get a distro that caters to that?

The LTS releases get interim updates.
And security fixes are released within the 6 months of a normal Ubuntu release.

And for many apps there are PPAs with cutting edge packages. Not always obvious? Right - but again, those who would have the most trouble dealing with those PPAs are the multitudes who don't care much to begin with.

And let's not forget that many are actually annoyed with applications changing all the time.

In short - this works according to plan - nothing to fix here. If the Ubuntu compromise is not to your taste you have alternatives available.

---

### Post by krazyd on 2010-05-18
> **Sophont said:**
> And most users will never notice. It's only a small percentage of us geeks who would notice (or even care) that some cool new feature is available upstream.
Exactly this. If you know enough about a package upstream to know about a cool new feature, then you know enough to upload it to your own ppa or find an updated ppa.

> **phrostbyte said:**
> I definately agreee with the idea. I've been saying it forever, Ubuntu needs better backports. Especially things like Firefox, to expect people to use an outdated Firefox for 4+ months is absurd.
10 seconds with google gave me:

firefox daily build ppa
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

firefox stable ppa
[https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable)

---

### Post by snowpine on 2010-05-18
> **krazyd said:**
> 10 seconds with google gave me:

firefox daily build ppa
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

firefox stable ppa
[https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable)

Not to mention the obvious:

[http://firefox.com](http://firefox.com)

No compiling from source necessary (despite claims to the contrary in this thread); you simply double-click on the executable, just like Windows.

---

### Post by Merk42 on 2010-05-18
> **Sophont said:**
> There is an unavoidable conflict between being almost cutting edge up-to-date and being well-tested and stable.


Is there?
I'm going to use Firefox as an example due to it's common use and rapid development:

Let's say Firefox 4 came out tomorrow.  There would be a bunch of threads in ABT asking how to install it (there were for 3.6, there were for 3.5...).  Also** Firefox 4 would have already gone through testing stages ie alphas and betas before being released**.


Yes I suppose you can get a PPA and/or download from the site, but if Ubuntu has trained people to go to Software Center/Update Manager for all their new and updated software, why should they be expected to know that a .x release as opposed to a .x.y release suddenly means they have to travel elsewhere? How would they know to look for a PPA or even what one is?

---

### Post by xebian on 2010-05-18
> **Merk42 said:**
> Is there?
I'm going to use Firefox as an example due to it's common use and rapid development:

Let's say Firefox 4 came out tomorrow.  There would be a bunch of threads in ABT asking how to install it (there were for 3.6, there were for 3.5...).  Also** Firefox 4 would have already gone through testing stages ie alphas and betas before being released**.


Yes I suppose you can get a PPA and/or download from the site, but if Ubuntu has trained people to go to Software Center/Update Manager for all their new and updated software, why should they be expected to know that a .x release as opposed to a .x.y release suddenly means they have to travel elsewhere? How would they know to look for a PPA or even what one is?

Does Windows/OSX even support Firefox?  No because Firefox caters to their needs. If Firefox releases deb files , end of story. The only support I know is making it not work properly or give those bogus error messages.

It's not instant as you'd like to have but for security patches I think Ubuntu isn't that bad/late.  As for newer versions I'm sure someone is tracking it.  It just takes time as it's reviewed and packaged/tested.

---

### Post by Merk42 on 2010-05-18
> **xebian said:**
> Does Windows/OSX even support Firefox?  No because Firefox caters to their needs. If Firefox releases deb files , end of story.

Okay then let's do a better analogy.

Internet Explorer: included by default and supported in Windows
Safari: included by default and supported in OSX

Guess what? IE automatically updated XPs browser from 6 to 7 to 8 without requiring users to buy Vista or 7
I'm pretty sure it's the same with Safari when it because default in Tiger.  Feel free to correct me there if I'm wrong.

---

### Post by tgm4883 on 2010-05-18
> **Merk42 said:**
> Okay then let's do a better analogy.

Internet Explorer: included by default and supported in Windows
Safari: included by default and supported in OSX

Guess what? IE automatically updated XPs browser from 6 to 7 to 8 without requiring users to buy Vista or 7
I'm pretty sure it's the same with Safari when it because default in Tiger.  Feel free to correct me there if I'm wrong.

To go further down this path. Does Canonical make FireFox? No. So why should they provide you with FireFox 4?

---

### Post by krazyd on 2010-05-18
> **Merk42 said:**
> Yes I suppose you can get a PPA and/or download from the site, but if Ubuntu has trained people to go to Software Center/Update Manager for all their new and updated software, why should they be expected to know that a .x release as opposed to a .x.y release suddenly means they have to travel elsewhere? How would they know to look for a PPA or even what one is?
If they don't, then they shouldn't be running an unsupported browser.

I suppose firefox.com could give a link to the stable firefox PPA or something. That way people could get the latest firefox in their package manager.

But again, that is something for Mozilla to sort out. They provide native installers for Windows, and Mac after all.

Really they should have something like this on firefox.com in addition to the tarball:
> [B]To add the repository for the latest firefox in Ubuntu, run:
```
sudo apt-add-repository ppa:mozillateam/firefox-stable
```
Then update your system as per normal.[/B]

It would be pretty minimal effort on their part. But then of course what about other distros?

Perhaps it's something for Canonical to talk to Mozilla about?

---

### Post by Merk42 on 2010-05-18
> **tgm4883 said:**
> To go further down this path. Does Canonical make FireFox? No. So why should they provide you with FireFox 4?

Okay let's keep going, then why support Firefox at all?

> **krazyd said:**
> If they don't, then they shouldn't be running an unsupported browser.

I suppose firefox.com could give a link to the stable firefox PPA or something. That way people could get the latest firefox in their package manager.

But again, that is something for Mozilla to sort out. They provide native installers for Windows, and Mac after all.

Really they should have something like this on firefox.com in addition to the tarball:


It would be pretty minimal effort on their part. But then of course what about other distros?

Perhaps it's something for Canonical to talk to Mozilla about?
I mentioned earlier in this thread, I'd concede to PPAs for the average user if they were more discoverable.



If a user dual boots, or even uses Windows at work and sees Firefox **automatically update** to the latest firefox, then they'd expect Ubuntu to do the same. Instead, they click update-manager, get confused it doesn't update, then posts one of many threads in ABT.

Here's a suggestion.  Firefox 4 comes out. In Ubuntu when a user starts 3.X a pop-up bar shows (like the 'know your rights' one).  Saying there is a new version of Firefox available.  Opting in would add the appropriate PPA with the understanding support would come from Mozilla, not Canonical.

---

### Post by snowpine on 2010-05-18
> **krazyd said:**
> If they don't, then they shouldn't be running an unsupported browser.

Ubuntu will never include an "unsupported browser." If 4.0 has some necessary security patch, Canonical will backport that patch to all currently supported Ubuntu releases through the Update Manager. You get all the security patches and bug fixes, just not the new features of the new release.

---

### Post by lykwydchykyn on 2010-05-18
It's a shame that questions like this end up being arguments over whose "fault" it is rather than a dissection of what the actual problem is and the best way it could be solved.

I guess I could point out to myself, as I've pointed out to others in the past, that it's moot anyway since few if any at this forum are in a position either to fix it or to impede its fixing. 

Whether or not a person thinks the current system is adequate, the forum traffic seems to reveal a fair number of people experiencing some difficulty.  That sounds to me like an opportunity for improvement -- not necessarily capitulating to every petty newbie demand, but to ask why this issue comes up again and again, and how it can be addressed.

---

### Post by tgm4883 on 2010-05-18
> **Merk42 said:**
> Okay let's keep going, then why support Firefox at all?

Good point. Maybe Canonical should rip FireFox from the archive. Or maybe the fact that they have packaged and offer something that is easily installable shouldn't opt them into a contract to provide future services? 

Maybe Canonical should do exactly what they say they are going to do.

> 
Canonical provides critical updates for firefox until April 2013.


I don't think FireFox 4 is a critical update

> **Merk42 said:**
> 
I mentioned earlier in this thread, I'd concede to PPAs for the average user if they were more discoverable.

Again, this links back to Mozilla not providing a .deb or PPA. It is rather easy to enable a PPA during the installation of a package. If Mozilla offered a PPA (or REPO) and .deb package themselves, something they seem unwilling to do. IMHO, I think this is what should probably be done. (which is a Mozilla issue, not a canonical issue)


> **Merk42 said:**
> 
If a user dual boots, or even uses Windows at work and sees Firefox **automatically update** to the latest firefox, then they'd expect Ubuntu to do the same. Instead, they click update-manager, get confused it doesn't update, then posts one of many threads in ABT.


IIRC, I don't think FireFox auto-upgrades itself on non-administrator level windows accounts. It tries to and usually fails.


> **Merk42 said:**
> 
Here's a suggestion.  Firefox 4 comes out. In Ubuntu when a user starts 3.X a pop-up bar shows (like the 'know your rights' one).  Saying there is a new version of Firefox available.  Opting in would add the appropriate PPA with the understanding support would come from Mozilla, not Canonical.

Wow, that seems like a great idea. Of course, that would have to be something implemented by Mozilla, which is what most of us have been saying for quite some time now.

---

### Post by jetsam on 2010-05-18
It's almost like the Mozilla foundation includes some strategically minded decision makers.  It sounds like you're suggesting that while Firefox is supportive of Linux, they have also decided not to spend precious resources supporting individual distros.

---

### Post by MCVenom on 2010-05-18
> **tgm4883 said:**
> Define trusted PPA
I believe the definition you would be looking for is in the USC roadmap :P

[https://wiki.ubuntu.com/SoftwareCenter#October%202010](https://wiki.ubuntu.com/SoftwareCenter#October%202010)

---

### Post by Sophont on 2010-05-18
> **Merk42 said:**
> 
I mentioned earlier in this thread, I'd concede to PPAs for the average user if they were more discoverable.

I agree that PPAs ain't for the average user. But neither is always looking for the most recent version and getting irritated if they get it a few weeks later. The average user won't even notice.

> **Merk42 said:**
> 
If a user dual boots, or even uses Windows at work and sees Firefox **automatically update** to the latest firefox, then they'd expect Ubuntu to do the same. Instead, they click update-manager, get confused it doesn't update, then posts one of many threads in ABT.

I don't believe that this is true for non-geek users.

The people around me (family, friends, etc...) that ask me for help about their computers *never* wonder whether they have the most up-to-date version of FF or otherwise. Unless they need a particular bug fixed most hardly bother to upgrade or inquire about anything.
They have a few programs they use, don't really want them to change much and are happy as long as things work.

The fact that on Ubuntu an application might be out-of-date (apart from security fixes) for a few weeks up to 6 months doesn't really affect most users.
Even if they see the windows FF updating - do you really think they bother to check and remember what version it is? For most the answer will be no.

And the minority who does care happens - mostly - to be the same minority who can handle PPAs.

This is a non-problem and not really worth wasting resources on IMHO.

p.s. Personally I would love to have well-tested updates for next months version. But I understand that trade-offs are involved and the compromise that Canonical settled on is OK.
There's always Debian, Arch, Gentoo etc... for anybody who needs the shiny super-fresh version.

---

### Post by MCVenom on 2010-05-18
> **snowpine said:**
> Not to mention the obvious:

[http://firefox.com](http://firefox.com)

No compiling from source necessary (despite claims to the contrary in this thread); you simply double-click on the executable, just like Windows.

No one has said it needs to be compiled. I've personally said that it's not in a format a new user would immediately understand, and that *I* tried to compile it in my n00bier days. But yeah, that executable isn't gonna upgrade Firefox, replace Firefox, import old settings, or add itself the the Gnome Menu.

Which is the whole point; every other OS does those things. :p

---

### Post by MCVenom on 2010-05-18
> **krazyd said:**
> If they don't, then they shouldn't be running an unsupported browser.

I suppose firefox.com could give a link to the stable firefox PPA or something. That way people could get the latest firefox in their package manager.

But again, that is something for Mozilla to sort out. They provide native installers for Windows, and Mac after all.

Really they should have something like this on firefox.com in addition to the tarball:


It would be pretty minimal effort on their part. But then of course what about other distros?

Perhaps it's something for Canonical to talk to Mozilla about?
Now, here's an idea! :D

---

### Post by nanog on 2010-05-18
I don't think anyone here is arguing that canonical should dedicate more resourced backporting. We are arguing that canonical/ubuntu could/should be doing more to promote the need for binaries (and the ease of use of their build services). 

> Perhaps it's something for Canonical to talk to Mozilla about?
If Vbox, Oo.o, opera, and chome can do this anyone should be able to. And I am not letting Oo.o off the hook for publishing fragmented debs instead of a metapackage. Forcing a user to install via dpkg is just silly.

> they have also decided not to spend precious resources supporting  individual distros. 	
That is absolutely no excuse. Debianized distros make up ~50% of desktop installs. And with the availability of packagekit they only need to support two binaries to cover 99% of linux. There are build services from novell and canonical that make this relatively easy.  

> It's because Firefox bias to Windows/OSX.  They should release debs  files 32/64-bit just like Opera, Google Chrome, OO, Virtualbox, others.   
Its not just mozilla. I ran Inkscape 0.47 stable from a ppa until I upgraded. A windows or mac user, on the other hand, only needed to download and click the installer.  Inexperienced users should not be using ppas. They will almost certainly fry their installs (and post that ubuntu should never be upgraded in the testing forum...grrrr).

---

### Post by nanog on 2010-05-18
> I don't think FireFox 4 is a critical update

As soon as Mozilla stops providing security updates it become, by definition, a critical update. This was a real headache in dapper and hardy and wasted a lot of dev time.

---

### Post by Sophont on 2010-05-18
> **Merk42 said:**
> Okay then let's do a better analogy.

Internet Explorer: included by default and supported in Windows
Safari: included by default and supported in OSX

Guess what? IE automatically updated XPs browser from 6 to 7 to 8 without requiring users to buy Vista or 7
I'm pretty sure it's the same with Safari when it because default in Tiger.  Feel free to correct me there if I'm wrong.

You're not wrong. But you're comparing apples to oranges.

First - no - you didn't need to buy Vista or W7 to get a new IE - but neither did you need to buy Ubuntu.
BTW ...
XP -> Vista: 6 years
Vista -> Vista SP3 - err sorry ;-)  - W7: 3 years

It then depends whether the windows user has updates set to update automatically (sadly I have to recommend everybody *not* to do that - see below).
If updates are not done automatically - people did not get an automatic upgrade to IE 7 or 8. Most non-geek users don't care or know how to do that. It's their geek friends who do that for them.

*If* they wanted to get IE 7 they had to also accept installing WGA. WGA is to be avoided IMHO as it provides 0 advantage to honest customers (the Genuine Advantage is for MS, not the customer) - and potentially gets the user in trouble in case of false positives or a server bug (both did happen).
(please note that I'm not talking about pirated copies of windows - only legit ones)

The problem with Windows auto-updating is not only the terrible WGA (of course unavoidable in the long run after W7 kills XP), but also that it wants to automatically reboot your computer all the time.
Anecdote: Recently my office machine died. I got a new one pre-configured and forgot to turn-off auto-update. It runs all the time because I access it via VPN a lot. One day I log in and wonder where all my open files went. The damn thing decided it's OK to reboot after updating and to hell with my open apps.

Of course if you don't keep up-to-date with security updates your windows gets owned by some phisher. Damned if you do - damned if you don't.

That's why I let Windows download automatically - but install manually - and skip a few updates (besides WGA, some driver updates could wreak havoc and SPs have to be handled carefully too - I know of some machines that don't like XP SP4).
The typical user without a personal tech-support geek at home is often screwed by MS updates.

Last but not least - the upgrade from IE (any version) is FF or Chrome or Safari or Opera. :-)
The last time MS thought it had safely conquered the browser market it dissolved the IE dev team and upgraded it once every hardly-ever.
MS would not be about to publish a mostly std-compliant IE9 if Mozilla hadn't forced them by cracking that IE monopoly.

It makes no sense to use IE and risk MS regaining it's browser monopoly. There is no reason to believe they would behave better next time.

The whole discussion (with regard to FF) will be moot when Firefox starts to self-upgrade itself as Chrome does (as is planned AFAIK).

---

### Post by rewyllys on 2010-05-18
> **Ellipsis said:**
> Although I love the Ubuntu release cycle and generally stick with the preinstalled software and versions, I like many others sometimes do need a more uptodate version of certain programs.

I concur completely in your pithily expressed point of view.  It certainly would be nice to be able to update my most used programs easily when updates of them become available, and such updates tend to appear on schedules quite unrelated to that of Ubuntu upgrades.

---

### Post by krazyd on 2010-05-18
> **snowpine said:**
> Ubuntu will never include an "unsupported browser." If 4.0 has some necessary security patch, Canonical will backport that patch to all currently supported Ubuntu releases through the Update Manager. You get all the security patches and bug fixes, just not the new features of the new release.

yeah but running 4.0 built from some unofficial PPA is not (and shouldn't be) supported by Canonical.

---

### Post by krazyd on 2010-05-19
> **Chauncellor said:**
> The point is to try and provide a slightly more convenient way of getting *unofficial* (but newer) versions of individual applications. This points toward a more community effort than a Canonical-induced one.

but my point is, this already exists:
```
**sudo apt-add-repository ppa:mozillateam/firefox-stable**
```

you don't even have to download an executable from some random website - the upgrade is already integrated in the OS!

We just need to get mozilla to stick that instruction on firefox.com along with the disclaimer that it is unsupported. (they should also give instructions on how to downgrade using ppa-purge)

> **Chauncellor said:**
> This kind of thing will feed the never-ending, idiotic flame-war about "which OS is better": Macs can't right click, Windows has viruses, Ubuntu can't upgrade firefox without using the command line, etc.

The command-line is an *asset*. I think it's more like
> Ubuntu can securely upgrade to the latest firefox with one simple command - no need to visit any random websites and manually download some random executable.

Honestly, don't you think it's safer/more secure/better to do everything from within the existing secure software management infrastructure?

Just because other OSs force users to go to some website and manually download and run some unsigned executable doesn't mean that's the way Ubuntu should do it. That's a major part of the whole virus problem in the first place.

---

### Post by Merk42 on 2010-05-19
> **krazyd said:**
> but my point is, this already exists:
```
**sudo apt-add-repository ppa:mozillateam/firefox-stable**
```
Actually the point is while it exists, it's not very discoverable. This results in many threads of "How do I upgrade Firefox" in Absolute Beginner Talk

> **krazyd said:**
> 
Just because other OSs force users to go to some website and manually download and run some unsigned executable doesn't mean that's the way Ubuntu should do it. That's a major part of the whole virus problem in the first place.
Other OSs don't do that though. When a user starts up Firefox, it says Oh hey new version! Upgrade? The user accepts and it's all done in the browser no download window or anything.

---

### Post by ranch hand on 2010-05-19
Well, I will have to say again, and this is just me, that one of the main reasons for switching to Linux was the CLI option.

Why, you may ask.  Well I am from the DOS era and had an awful time adjusting to what ever MS called that thing before W95.  Don't get me wrong here, it worked but the change was kind of extreme.

It still had a robust CLI which quickly disappeared in 95.  I had little experience with 95 but used 98 for a long time.  The CLI, in my opinion, was removed from MS products because it made the GUI look bad.  There are many things that it is just faster and easier to use the terminal for.

I generally use the GUI.  I am not really fluent in geek.  The CLI does not force you to know a lot of commands.  A very little study will get you all the commands that are going to be handy for you.

Just because other OS' are turning out product for the hard of learning does not mean that Linux in general or Ubuntu in particular should go that route.

If some one is too idiotic to learn a few basic commands they should probably not be turned loose on ANY OS.  We see these whiny folks here on the forums as in "well it works this way in MS" or "MAC does it this way".

OK, so what?  There really are those of us that switched, not to be cool, not to avoid paying for an OS, but because the "user experience" is already a whole long way out in front of those crappy other platforms.

I, and again this is me, do not like the idea of down grading Ubuntu because some people are too dumb to use it.  There is an OS out there for them right now.  It is perfect for them.  It even has a function to tell them how much they are enjoying it.  It is call MS (I always thought MS was an ailment that causes degeneration of the nervous system so I think the name MS is fine for that product).

---

### Post by Penguin Guy on 2010-05-19
Yes, let users choose weather to use the stable version or the newer version.

---

### Post by snowpine on 2010-05-19
The hardest word in the English language to say is "No." :)

Q: "Dear Canonical, can you please make it easier to replace the stable application versions in the Ubuntu repositories with the latest versions, without using the command line?"

A: "No. Our official support for upgrades is through the 6-month release cycle, which we believe provides the best balance between freshness and stability for our target users."

I really respect Canonical for their clarity on what they do, and do not, support. There is a strange assumption in this thread that first-time Linux users should not try the default methods for a release or two before they try to upgrade the system on their own. :)

---

### Post by snowpine on 2010-05-19
> **Chauncellor said:**
> It's great that you want it, but Ubuntu is not a CLI distro. There are others for that. This is "Linux for Human Beings", which ultimately means a nice, easy GUI for the user.

I cannot agree with this statement. Human Beings learned how to communicate with words and symbols millenia before they learned how to click shiny icons. 

The CLI is an unambiguous and universal format, compared with GUI instructions like "go to the applications menu at the top left of your screen, choose internet, and click the purple penguin" that may be misinterpreted depending on the user's desktop environment, theme, settings, language, visual ability, etc.

I am not being "elitist" and dictating that all users must use the CLI, but rather stating the obvious reason why it is the preferred method for exchanging information with other users via the internet.

---

### Post by ranch hand on 2010-05-19
> **Chauncellor said:**
> Ranch Hand, you're thinking with a bit of an elitist attitude. Should people not be allowed to drive cars because they can't fix them? Can you give a western harmonic analysis the music you listen to? If not, maybe you shouldn't be allowed the pleasure. The list can go on. People just want something that works. They are busy fixing your car, or teaching your children, and so on. Again, this is a different age. Whether or not we are spoiled with GUI is something, but the fact remains that people will not want to deal with this kind of thing.

The thing is, Ubuntu is aiming to be an OS for all the users; the type of "program" that Firefox has succeeded in spreading usage. The farthest people probably ever will go with that program is about:config, which hardly equates to CLI. I'm not saying that CLI is a *bad* thing and must be abolished, but people do **not** want to use it! Have you ever used Mac's CLI? It's just as useable and amazing as any Linux distro. Yet (like I stated earlier) Mac users just don't use it unless they want to. It's great that you want it, but Ubuntu is not a CLI distro. There are others for that. This is "Linux for Human Beings", which ultimately means a nice, easy GUI for the user.

Why on earth do we need GParted on the LiveCD? Why not just let everyone learn CLI partitioning, and the "pinheads" that don't want to learn just not be able to use the functionality?

I feel that the heart of the discussion has been lost and transformed, so there's probably little use in continuing a debate.
I do not believe you actually read my post.

I was fairly clear that I generally use a gui.  I am not an expert on  CLI and see no reason to be.

The only place that I see the terminal to be really needed is here in  testing.  I still do use it in 8.04, 9.04 and 10.04, primarily for  updates.  Very much faster.

With the addition of "nautilus-gksu" you do not even need the terminal  to edit system files.

If folks are being "forced" to use the terminal under Ubuntu, I just  can't see where.

There are uses for the CLI partitioning agents.  I prefer Gparted as it is safer for  me to use it.  Some of the CLI ones are too much for me to handle (sfdisk).  I do like cfdisk quite a bit but I only use it where I have to use something like DSL and partition a box with little ram, I haven't screwed a drive yet with it.

Getting to it is tough to learn if you are illiterate.  You do have to type in sudo cfdisk.  After that it is pretty self explanatory or I, seriously, couldn't use it.

---

### Post by snowpine on 2010-05-19
> **Chauncellor said:**
> Maybe the PPAs certainly are the best method. Maybe this entire thread has shown that things really are the best as they are now. Again, I've just been trying to find my own opinion on the best route through these "devil's advocate" posts.

I don't have a definitive answer either, and I'm enjoying the conversation. Please keep the "devil's advocate" posts coming! :)

---

### Post by ranch hand on 2010-05-19
I have to agree that the level of ignorance is impressive.

I do not feel I am being modest.  Out here you are your own tech support, not just for computers but pretty much everything.  We pretty much fight our own wild fires too.  A good understanding of your tools is necessary.  I do not, in anyway, feel real "up to it" on computers.

Maybe the partition problem is that they are all my age and first learned on computers with no hard drive, just floppies.

---

### Post by lykwydchykyn on 2010-05-19
> **snowpine said:**
> The hardest word in the English language to say is "No." :)

Q: "Dear Canonical, can you please make it easier to replace the stable application versions in the Ubuntu repositories with the latest versions, without using the command line?"

A: "No. Our official support for upgrades is through the 6-month release cycle, which we believe provides the best balance between freshness and stability for our target users."

I really respect Canonical for their clarity on what they do, and do not, support. There is a strange assumption in this thread that first-time Linux users should not try the default methods for a release or two before they try to upgrade the system on their own. :)

What's the -backports repository for again?

---

### Post by seeker5528 on 2010-05-19
> **nanog said:**
> Those who talk about stability are missing the point.

Those who talk about stability, probably expect stability.....

No introduction of software that could change behavior in unexpected ways, break user created scripts, cause user installed add-ons to stop working, 3rd party software to stop working, etc.... unless such an update is necessary to fix a security issue.

> Its time for linux and Ubuntu to actively discourage the antiquated tarball release mechanism.

It's not up to Ubuntu to discourage this, there is plenty of software for window being provided as a zip file, I've never heard of MS doing anything to discourage it.
 
> (I think this is also an argument for Ubuntu to work more closely with Debian to make sure we do not stray too far from our roots.)

I think it's an argument that more should be done through the LSB to provide something ISVs will use to package software. In the mean time, many projects rely on people using a distro to provide a package or packages for that distro, people interested providing distribution independent packages could always supply a foobar.lsb-version.architecture.rpm package.  

Working more closely with Debian is always something to be applauded though.

Later, Seeker

---

### Post by krazyd on 2010-05-19
Upstream projects already use the option of supplying an "official" PPA (the best option IMHO):
[http://smplayer.sourceforge.net/downloads.php?tr_lang=en](http://smplayer.sourceforge.net/downloads.php?tr_lang=en)

Others supply .deb's:
[http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/post-download/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/post-download/)

I still don't really see how either of these options are worse than Mac/Win. The PPA option is actually better IMHO because the packages are signed.

A downloaded .deb could even add its PPA to your repository list the first time it is installed to get future updates automatically..

---

### Post by MCVenom on 2010-05-20
> **krazyd said:**
> Upstream projects already use the option of supplying an "official" PPA (the best option IMHO):
[http://smplayer.sourceforge.net/downloads.php?tr_lang=en](http://smplayer.sourceforge.net/downloads.php?tr_lang=en)

Others supply .deb's:
[http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/post-download/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/post-download/)

I still don't really see how either of these options are worse than Mac/Win. The PPA option is actually better IMHO because the packages are signed.

A downloaded .deb could even add its PPA to your repository list the first time it is installed to get future updates automatically..
It's great that projects provide these (had no clue Firefox had an official PPA); I guess the question now is, wy aren't they somewhere where a new user can find them?

---

### Post by 23meg on 2010-05-20
> **lykwydchykyn said:**
> What's the -backports repository for again?

It's for backporting libraries and applications that are already in the development branch at any given time. Which means that those that aren't can't be backported, that one needs to take the effort to get things working with the development branch (which is a moving target) first just to be able to ship updates to the most recent stable release, and that an upstream or individual developer who isn't willing to put the effort in to coordinate with the Ubuntu development community to get their new software (or updates) into the development branch and/or package it themselves and submit it for inclusion in Universe (or get per-package upload privileges, as per the recent archive reorganization effort) is out of luck, unless they're in contact with someone who is.

---

### Post by 23meg on 2010-05-20
> **BlackOtaku said:**
> It's great that projects provide these (had no clue Firefox had an official PPA); I guess the question now is, wy aren't they somewhere where a new user can find them?

The most obvious reason is that at present, there's no established technical mechanism and corresponding community process through which to ensure the "official"ness and trust level a of PPA.

---

### Post by krazyd on 2010-05-20
> **23meg said:**
> The most obvious reason is that at present, there's no established technical mechanism and corresponding community process through which to ensure the "official"ness and trust level a of PPA.

A link to a PPA on upstream's website is at least as official as putting up a link to an executable installer (like windows).

---

### Post by 23meg on 2010-05-20
> **krazyd said:**
> A link to a PPA on upstream's website is at least as official as putting up a link to an executable installer (like windows).

That's enough for the "visit upstream's website, discover PPA, add it, install" case, but not for determining which PPAs are trusted by whom, and establishing a "web of trust" mechanism.

---

### Post by zekopeko on 2010-05-20
> **23meg said:**
> That's enough for the "visit upstream's website, discover PPA, add it, install" case, but not for determining which PPAs are trusted by whom, and establishing a "web of trust" mechanism.

See if there is a package in Debian or Ubuntu and then you can add the users friends on top of that. High-profile apps can have a deal with Canonical to guarantee quality.

---

### Post by 23meg on 2010-05-20
> **zekopeko said:**
> See if there is a package in Debian or Ubuntu and then you can add the users friends on top of that. High-profile apps can have a deal with Canonical to guarantee quality.

I don't understand the first sentence (clarify?), but yes, some trusted upstreams that work with the development community can perhaps have their PPAs listed but disabled by default in USC, with clear descriptions to keep people aware of what would happen if they were to enable them, similar to how, for example, Firefox ships a few root authority certificates for parties they trust to be authentic and reliable.

---

### Post by nanog on 2010-05-20
More on stability.

I use upstream packages  because for me they are often more stable than ubuntu's. In every case, the install for these major applications is point &  click for mac and windows but is typically a hassle in linux. I consider a set of trusted application ppas that are accessible in the software center  to be essential for solving bug #1. 

I would be very happy if ubuntu/canonical worked with upstream to make this happen.

---

### Post by BwackNinja on 2010-05-20
> **Chauncellor said:**
> Ranch Hand, you're thinking with a bit of an elitist attitude. Should people not be allowed to drive cars because they can't fix them?....

I have to agree with Ranch Hand, and I'd change your metaphor around a little too. People should not be allowed to drive stick if they cannot change gears. Let them stay with automatic. No matter what changes you make to a car with a stick shift, no matter how much easier you make it to change gears, if the driver refuses to do so, the car is still wrong for them. The point is that there are benefits to using an open-source operating system, much like there are benefits to driving a stick shift. If these benefits are meaningless to the user, and they only complain about the extra work, then the system is not for them.

There is a driving test to ensure that people don't drive like they play bumper-cars. There is no such test for computers, so we must pave the road with pillows to make sure no one gets hurt. The pillows are best used at the sharp turns, and it takes a long time to make sure there is a pillow everywhere, but the big question is should we *have* to put one everywhere?

Now, directly on topic:

The ideal situation here is not for backports to be used a lot. People would care about an update to individual applications, not a bunch of them. If they wanted all of them always, a rolling-release distro is for them. Instead, what we'd want would be an indicator, much like we have a new stable release indicator (though I can't think of an appropriate place), where you can upgrade to a new version if you want to, and it will set all that up for you. There should not be development versions there, only stable, community-tested updates that do _not_ mess with any important system libraries, maybe only a couple that are only used by that program. Support would need to be added to Software-Center, but the biggest part is to have a set of trusted repos that anyone can add without worrying that what they get will be nonworking, as well as a nice undo button, which in this case would easily be powered by ppa-purge.

---

### Post by zekopeko on 2010-05-21
> **23meg said:**
> I don't understand the first sentence (clarify?), but yes, some trusted upstreams that work with the development community can perhaps have their PPAs listed but disabled by default in USC, with clear descriptions to keep people aware of what would happen if they were to enable them, similar to how, for example, Firefox ships a few root authority certificates for parties they trust to be authentic and reliable.

If the package is in Debian or Ubuntu and was signed by somebody that is either part of the upstream or part of Debian/Ubuntu. You can add an agreement with Canonical to have some QA and have them in USC by default or at least recommended.

The problem are personal PPAs. They could be "trusted" in the form of "23 people and 6 of your friends are using this PPA".

---

### Post by MCVenom on 2010-05-21
> **BwackNinja said:**
> The ideal situation here is not for backports to be used a lot. People would care about an update to individual applications, not a bunch of them. If they wanted all of them always, a rolling-release distro is for them. Instead, what we'd want would be an indicator, much like we have a new stable release indicator (though I can't think of an appropriate place), where you can upgrade to a new version if you want to, and it will set all that up for you. There should not be development versions there, only stable, community-tested updates that do _not_ mess with any important system libraries, maybe only a couple that are only used by that program. Support would need to be added to Software-Center, but the biggest part is to have a set of trusted repos that anyone can add without worrying that what they get will be nonworking, as well as a nice undo button, which in this case would easily be powered by ppa-purge.

This was the idea I was going for, so I'd have to say I agree. :D

---

### Post by ronacc on 2010-05-21
> **zekopeko said:**
> If the package is in Debian or Ubuntu and was signed by somebody that is either part of the upstream or part of Debian/Ubuntu. You can add an agreement with Canonical to have some QA and have them in USC by default or at least recommended.

The problem are personal PPAs. They could be "trusted" in the form of "23 people and 6 of your friends are using this PPA".

perhaps a separate section of USC that has to be enabled by the user , with appropriate warnings and disclaimers ( here there be tygres ) , that takes one outside the "normal" upgrade path and also instructions about how to file bugs on "non normal" packages .

---

### Post by cgroza on 2010-05-21
They already have enough in their heads... without updating and fixing the new versions of software...

---

### Post by nanog on 2010-05-21
> They already have enough in their heads... without updating and fixing  the new versions of software...I don't think anyone is asking for this. I want ubuntu users to have the same ability to easily upgrade to STABLE releases of firefox, flash, open office, thunderbird, virtualbox that windows and mac users have. This new trusted PPA mechanism would be a very cool solution -- especially if it is accessible in the USC. We just need to get mozilla, oracle, adobe, and google to support this mechanism.

---

### Post by zekopeko on 2010-05-21
> **ronacc said:**
> perhaps a separate section of USC that has to be enabled by the user , with appropriate warnings and disclaimers ( here there be tygres ) , that takes one outside the "normal" upgrade path and also instructions about how to file bugs on "non normal" packages .

I wouldn't put it so prominently. From the top of my head I would put an option inside the App view (you know, text+screenshot etc).

---

### Post by zekopeko on 2010-05-21
> **nanog said:**
> I don't think anyone is asking for this. I want ubuntu users to have the same ability to easily upgrade to STABLE releases of firefox, flash, open office, thunderbird, virtualbox that windows and mac users have. This new trusted PPA mechanism would be a very cool solution -- especially if it is accessible in the USC. We just need to get mozilla, oracle, adobe, and google to support this mechanism.

Well that is development model problem. Mozilla and Chromium for example use patched versions of various libaries. So if you allow this model you get Windows and OSX where every app ships a separate library. That means overhead when bugs are found in those libraries. Ubuntu now can patch a single library and fix a bug in a bunch of applications.

---

### Post by seeker5528 on 2010-05-21
> **BwackNinja said:**
> I have to agree with Ranch Hand, and I'd change your metaphor around a little too. People should not be allowed to drive stick if they cannot change gears. Let them stay with automatic.

Don't know how well that fits either. I find it hard to believe someone would not be able to shift a stick with an automatic clutch.

That's not to say they wouldn't choose inappropriate times to shift, but that a different problem. :P

Later, Seeker

---

### Post by ronacc on 2010-05-21
> **zekopeko said:**
> I wouldn't put it so prominently. From the top of my head I would put an option inside the App view (you know, text+screenshot etc).

no I don't know , where is this App view ? I don't see it in the current USC (2.1.1 )  or in the blueprint for 3.0  . also is there a ppa for 3.0 yet ( or source , I don't mind building)  I'll give it a spin .

---

### Post by seeker5528 on 2010-05-21
> **zekopeko said:**
> Well that is development model problem. Mozilla and Chromium for example use patched versions of various libaries.

That in and of it's self is not a problem. 

>  So if you allow this model you get Windows and OSX where every app ships a separate library.

If we want the "easy installation" experience that people claim windows has, that's necessary. Otherwise a lot of software needs to be packaged specifically for your distribution. If it's packaged specifically for your distribution dependencies are an issue. You can't have it both ways.

The compromise is LSB compliant packages. By definition LSB compliant packages must include their own copy of anything not covered by the LSB, so you get relatively easy installation. No dependency issues to speak of. Uninstallation using the same methods that you use for your distribution vendor supplied packages.


> That means overhead when bugs are found in those libraries.

An issue if a bunch of the included software uses their own versions. If people are getting the upstream/ISV supplied software, there is no cost to Ubuntu developers. 

> Ubuntu now can patch a single library and fix a bug in a bunch of applications.

That is why you generally want to stick to packages from the official repositories.

Certainly for some range of stuff it would be preferable to have packaged for for your distribution.

IMHO, for a large percentage of stuff it would be preferable to have LSB compliant packages. No dependency issues to speak of. They wouldn't replace the stuff acquired through officially supported distribution channels, so wouldn't break other software that depends on those distribution vendor supplied versions. You would still be getting the normal security updates for the versions supplied through the officially supported channels so that alleviates the security concern as it relates to other software that uses features supplied by those things.

If I can go to some random web page and download a .deb file, open the file manager, click on that .deb file and have the installation automated along with any dependencies that are available from any of the sources in my sources.list file. I don't understand why I don't have the option to go to some random web page, download a .lsb-version.architecture.rpm, open the file manager, click on the lsb compliant package, and have the installation automated from the check that support for the necessary version of the LSB is available, to the installation of the required LSB components if they are available but not installed, to the calling on alien to convert and install the downloaded package. 

Later, Seeker

---

### Post by Scotty Bones on 2010-05-21
I ran into this very issue just today with virtualbox. 

update-manager wanted to update from 3.1.6 to 3.1.8 while 3.2 is just chillin' there in synaptic (which I would not have know of had VB not informed me of the update). Is it really so hard to get with the program here, I'm mean seriously. Why should I have to deal with these updates manually? Upgrading to newer versions of programs should not be a pain in rear for the average user. There has to be an easier method of handling this with a more automated process.

For myself this isn't a big deal,just an annoyance; but as a technician, I'm often forced to view issues from the prospective of the average user. And the current situation is not average user friendly. **It's a problem**, and it needs to be addresses in a more visible and accessible way for average users.

---

### Post by jetsam on 2010-05-21
We need to root out the hidden agenda that prevents a universal installer from being accepted.  Bruce Perens is next.

---

### Post by zekopeko on 2010-05-21
> **seeker5528 said:**
> That in and of it's self is not a problem. 

If we want the "easy installation" experience that people claim windows has, that's necessary. Otherwise a lot of software needs to be packaged specifically for your distribution. If it's packaged specifically for your distribution dependencies are an issue. You can't have it both ways.

The compromise is LSB compliant packages. By definition LSB compliant packages must include their own copy of anything not covered by the LSB, so you get relatively easy installation. No dependency issues to speak of. Uninstallation using the same methods that you use for your distribution vendor supplied packages.

An issue if a bunch of the included software uses their own versions. If people are getting the upstream/ISV supplied software, there is no cost to Ubuntu developers. 

That is why you generally want to stick to packages from the official repositories.

Certainly for some range of stuff it would be preferable to have packaged for for your distribution.

IMHO, for a large percentage of stuff it would be preferable to have LSB compliant packages. No dependency issues to speak of. They wouldn't replace the stuff acquired through officially supported distribution channels, so wouldn't break other software that depends on those distribution vendor supplied versions. You would still be getting the normal security updates for the versions supplied through the officially supported channels so that alleviates the security concern as it relates to other software that uses features supplied by those things.

If I can go to some random web page and download a .deb file, open the file manager, click on that .deb file and have the installation automated along with any dependencies that are available from any of the sources in my sources.list file. I don't understand why I don't have the option to go to some random web page, download a .lsb-version.architecture.rpm, open the file manager, click on the lsb compliant package, and have the installation automated from the check that support for the necessary version of the LSB is available, to the installation of the required LSB components if they are available but not installed, to the calling on alien to convert and install the downloaded package. 

Later, Seeker

I agree with you that the current situation isn't ideal.

What I would want to see is:

A way for the user to install an application in their Home directory. Klik2 promised that but nothing has happened for years with it. It would run in a sandbox so that malicious apps can't do damage to the users home. 

If another users tries to install the same app it would simply use the one that is already in another users directory. There was a project that permitted exactly that (I think it was a part of some university work).

Applications that need to ship newer libraries then the one currently available in the distro would first try and use the system ones and then fall back on their own. The support would come from upstream and not from Canonical for those packages.

The point is that the libraries that Ubuntu ships with (both on the CD and in the repos) shouldn't be overwritten.

The problem is what I said before. There is a larger surface area for bugs and security vulnerabilities. Some upstream aren't so active and they don't support older releases. ffmpeg comes to mind here.

All of this should be for advanced users. Observing my family in their interaction with computers, I have concluded that they simply don't care for the "next hot version" of some program. They just want it to work. If I didn't upgrade the software they use they would still use Firefox 2 or would call me in semi-panic when an app pops up an update window.

I think that the policy that is being implemented in Maverick is going to help alleviate problems in this area at least for new apps. I'm talking about having new applications in the repos that aren't a part of them when Ubuntu freezes them. Please note that this applies only to new apps that don't need newer libraries then the ones that a currently frozen in Ubuntu.

---

### Post by jetsam on 2010-05-21
I really have no idea.  I get the sense it's not that hard, but everybody wants to do it their way.

---

### Post by ronacc on 2010-05-21
One of the problems is the diversity embraced by Linux ( it is also one of our strengths ) , Apple is positively anal about controlling how things are done and Microsoft only slightly less so and both are very monolithic . We have over 100 distros each with its own way of doing things which makes a truly universal installer virtually impossible . To go the way of each app installing its own set of libs is unacceptable because it leads to the kind of insane bloat you see in windows . One possible way out would be for newer libs to "contain" the older lib as a subset , IIRC that was the way the Amiga handled it , if something like that could be implemented and if an honest effort was made to do things that way it would go a long way to resolve the problem .

---

### Post by Longinus00 on 2010-05-22
> **Scotty Bones said:**
> I ran into this very issue just today with virtualbox. 

update-manager wanted to update from 3.1.6 to 3.1.8 while 3.2 is just chillin' there in synaptic (which I would not have know of had VB not informed me of the update). Is it really so hard to get with the program here, I'm mean seriously. Why should I have to deal with these updates manually? Upgrading to newer versions of programs should not be a pain in rear for the average user. There has to be an easier method of handling this with a more automated process.


Virtualbox does this because 3.1.6 to 3.1.8 is a bugfix release while 3.1.* to 3.2.* is a major release. You're less likely to have regressions upgrading from 3.1.6 > 3.1.8 than 3.1.* > 3.2 That's the whole point behind the versioning scheme. This is rather important information to sysadmins.
[http://en.wikipedia.org/wiki/Software_versions#Change_significance](http://en.wikipedia.org/wiki/Software_versions#Change_significance)

> **Scotty Bones said:**
> 
For myself this isn't a big deal,just an annoyance; but as a technician, I'm often forced to view issues from the prospective of the average user. And the current situation is not average user friendly. **It's a problem**, and it needs to be addresses in a more visible and accessible way for average users.

You are projecting. It **not a problem** because the average user doesn't care what he has installed, so long as it works. Look at the prevalence of old browsers/operating systems here [http://www.w3counter.com/globalstats.php](http://www.w3counter.com/globalstats.php) More page hits with ie 6 than with osx.

---

### Post by zekopeko on 2010-05-22
> **ronacc said:**
> no I don't know , where is this App view ? I don't see it in the current USC (2.1.1 )  or in the blueprint for 3.0  . also is there a ppa for 3.0 yet ( or source , I don't mind building)  I'll give it a spin .
It's called Software Item screen in the spec: [https://wiki.ubuntu.com/SoftwareCenter#Software item screen](https://wiki.ubuntu.com/SoftwareCenter#Software item screen)

---

### Post by ronacc on 2010-05-22
thankyou .

---

### Post by Merk42 on 2010-05-22
> **Longinus00 said:**
> 
You are projecting. It **not a problem** because the average user doesn't care what he has installed, so long as it works. Look at the prevalence of old browsers/operating systems here [http://www.w3counter.com/globalstats.php](http://www.w3counter.com/globalstats.php) More page hits with ie 6 than with osx.

A lot of IE6 use comes from corporate environments where the user CAN'T upgrade/use a different browser.

---

### Post by snowpine on 2010-05-22
> **Merk42 said:**
> A lot of IE6 use comes from corporate environments where the user CAN'T upgrade/use a different browser.

Bingo. :) If Ubuntu wants to gain inroads with corporate customers, they need to stick with the current stable release system. Upgrading for the sake of upgrading is a bad idea in a business environment.

---

### Post by ranch hand on 2010-05-22
I have no idea why we should be the least interested, or concerned, with what folks do with IE or any other app that belongs on another, unrelated OS.

The only way Linux in general and Ubuntu in particular is going to be more wide spread is to be different.

If it is the same, why change?

I can only speak for me, of coarse, but I switched from MS to Linux.  No dual boot (did have a separate drive to swap in if needed for 3 weeks).  Ubuntu was the first I tried as it was recommended by my son.

It was not the only one I tried.  I liked some, didn't like others.  There is not one of them that I would not use if the other choice was MS.

Why?  Because the "user experience" is so much better in Linux than in MS.  This is even true although none of the Linux OS' I have tried even have an app to tell me how much I like it.

My goodness, I should start another silly thread suggesting that Ubuntu should, for the sake of getting more broad approval, have just such an app.  It could come up when you log in or out  or both and say "Hey You are Really Happy with Ubuntu at xy%".

Right after a crash, like in MS, would be best though.

---

### Post by snowpine on 2010-05-22
> **ranch hand said:**
> The only way Linux in general and Ubuntu in particular is going to be more wide spread is to be different.

If it is the same, why change?

Well said! :KS

---

### Post by Longinus00 on 2010-05-22
> **Merk42 said:**
> A lot of IE6 use comes from corporate environments where the user CAN'T upgrade/use a different browser.

Did you gloss over how many people are on windows xp? How about people more people using firefox 3 than linux? Ie 7 users?

---

### Post by Merk42 on 2010-05-22
> **Longinus00 said:**
> Did you gloss over how many people are on windows xp? How about people more people using firefox 3 than linux? Ie 7 users?

I don't understand what you're getting at.

My point was it seemed like you were saying "oh look so many people use IE6, guess they don't care to upgrade" and I was saying that a good amount of those people are using IE6 because they don't have any other option.

---

### Post by snowpine on 2010-05-22
> **Merk42 said:**
> I don't understand what you're getting at.

My point was it seemed like you were saying "oh look so many people use IE6, guess they don't care to upgrade" and I was saying that a good amount of those people are using IE6 because they don't have any other option.

Not quite; in your example, they are indeed still using IE6 by choice--their boss's choice! :) You'll find that management often sticks with older software versions that fit their business needs, rather than incur the cost, uncertainty, and disruption of upgrading to the latest version. 

When considering that many corporations are still using a 9-year-old browser, Ubuntu's 0-to-6-month-old Firefox policy looks positively cutting-edge. :)

---

### Post by jetsam on 2010-05-22
> **snowpine said:**
> Not quite; in your example, they are indeed still using IE6 by choice--their boss's choice! :) You'll find that management often sticks with older software versions that fit their business needs, rather than incur the cost, uncertainty, and disruption of upgrading to the latest version. 

When considering that many corporations are still using a 9-year-old browser, Ubuntu's 0-to-6-month-old Firefox policy looks positively cutting-edge. :)

Plus one insightful.  The software landscape is stuck in the past decade because it is primarily commercial on the client side.

Add in the fact that the entire internet is vulnerable because the client side is a sewer.

There's no getting around it.

Bug #1 is a political issue.  Primarily, we've already solved the technical troubles in 1000 different ways.

The thing is.. just by standing our ground.  Just because bug number one stays there.

Redmond looks poorer and poorer every day.

It's a fat uncle now.  The one that the entire family doesn't trust.  Because that uncle drinks the hard stuff, and he can't stop.  

And we liked our Auntie better before he drove her off.  

We're glad she's safe, but we're sick to death of our Uncle Paperclippy-- and everything he exhausts, every ugly thing that he produces.

---

### Post by seeker5528 on 2010-05-22
> **jetsam said:**
> We need to root out the hidden agenda that prevents a universal installer from being accepted.

I really don't think there is any hidden agenda.

My interpretation of the situation is.....

As it relates the the LSB, the initial failing is that the packaging spec was derived from what distribution vendors do with the native package management without really consulting ISVs to determine what capabilities should be there to make the idea of distributing LSB compliant packages attractive to them. I think some time was spent addressing that issue with LSB 4, but there probably still needs to be more advancement in that area. Since LSB compliant packages only use a subset of RPM and can only depend on things covered by the LSB, dealing with these packages in distributions that don't use RPM for their native package management is a non-issue.

Outside of the LSB you have divergent ideas about what "universal installer" even means and confusion about what is needed for a universal package installation relative to native package installation.

Distributions are managed systems, differences in native package formats, libraries, and other potential incompatibilities that may prevent packages created for one distribution from being installed in another distribution are a non-issue, you shouldn't be using packages created for another distribution as a way to upgrade/replace packages that are native to your distribution.   

Projects that start with the idea that they can provide "universal installation" by replicating package management in a non-distribution specific way using non-native packages to 'overcome the evils of native package management' are, IMHO, starting with a bad concept to begin with, so will always be limited in their uptake.

From my viewpoint a universal installer only need 4 things to be successful.

[list]1: Be accepted by ISVs.[/list]
[list]2: Easy for the users.[/list]
[list]3: Don't replace or interfere with anything installed using the distributions native officially supported mechanisms/channels.[/list]
[list]4: During installation the necessary information is provided to the native package management system so removal is the same as it is for the native packages.[/list]

LSB compliant packages take care of 3 and 4, 1 is a work in progress. 

For 2, it's not hard to deal with LSB compliant packages in a distribution where RPM is not the native format if you know which LSB-* packages are required and know how to use alien, and instructions can be provide for those who don't know. It doesn't seem any harder to me than going to mozilla.com, downloading Firefox and installing it.

If we saw more projects providing LSB compliant packages, it doesn't seem like it should be all that hard for an interested developer to create utilities that provide functionality equivalent to apt-url and gdebi, that use package kit to check whether the necessary LSB support is installed and if not offers to install the packages that provide the support, then depending on the distribution uses rpm or alien to install the package.

Later, Seeker

---

### Post by ranch hand on 2010-05-22
While I do not see a need for LSB at all, I certainly agree that there is no hidden agenda.

There is simply the fact that this is Linux and folks have;
A>freedom of choice
B>favorite package management systems
C>fear of assimilation into a universal system

I think all three are some of the strengths of Linux.

There will be, someday, a universal package management system.  Users will decide this by using it instead of the others.

I do not like RPM as a system.  There are a lot of folks that do and I can see why.

I like .deb as a system.  There are a lot of folks that do not and I can see why.

Some of the other systems are pretty weird to me.  One of them, or a new one, may evolve into that elusive universal package manger.

Therefore I would not push too hard on this for 2 reasons;
1>it is stifling
2>it is a waste of time like beating your head on the wall

---

### Post by nanog on 2010-05-22
> Microsoft only slightly less so and both are very monolithic

Actually this is not correct. There is no standard installer in windows. In fact, there is a far larger hodgpodge of proprietary and open source installers in windows than there is in linux. Technically the two major linux package systems (rpm and deb) are superior to what is done in windows or osx -- its just user experience that is a fail. 

PS: I believe windows is now looking very hard at incorporating linux-type package systems in windows. Frankly, I think they should just admit defeat and use linux...

---

### Post by ronacc on 2010-05-22
> **nanog said:**
> Actually this is not correct. There is no standard installer in windows. In fact, there is a far larger hodgpodge of proprietary and open source installers in windows than there is in linux. Technically the two major linux package systems (rpm and deb) are superior to what is done in windows or osx -- its just user experience that is a fail. 

PS: I believe windows is now looking very hard at incorporating linux-type package systems in windows. Frankly, I think they should just admit defeat and use linux...

I believe the is a "standard installer" in windows it is just often ignored . 

and good lord no they would wreck it completely .

---

### Post by Merk42 on 2010-05-22
> **snowpine said:**
> Not quite; in your example, they are indeed still using IE6 by choice--their boss's choice! :)
Oh okay so I guess 100% of natives of {insert country} made the same choices as their leader
 > **snowpine said:**
> You'll find that management often sticks with older software versions that fit their business needs, rather than incur the cost, uncertainty, and disruption of upgrading to the latest version. 
Um, I know that's what I was saying.

---

### Post by seeker5528 on 2010-05-22
> **ranch hand said:**
> While I do not see a need for LSB at all, I certainly agree that there is no hidden agenda.

Universal installation needs standardization, that's what the LSB is for. Getting from LSB 1 to LSB 4 has been a long road, but it's far enough along now that it would be reasonable to ship many desktop and multimedia type software as LSB compliant packages, but at the same there is still a lot of stuff where it doesn't make sense.

> There will be, someday, a universal package management system.  Users will decide this by using it instead of the others.

Even if all distributions used the same package management system, that doesn't change the issues. Distributions all have their own design goals, different types of users targeted, different types of hardware, different environments and use cases for said hardware and distributions.

To me package management and universal installation are different problems that need different solutions.

In Windows what management there is is provided by windows update. You don't go to Windows update to look for updates for stuff that is not provided by Microsoft. Typically, if you value your sanity, you don't try to replace parts of the managed windows system with stuff that was created/modified by a 3rd party that doesn't come through offical MS channels, but for IE, Media Player, Media Center, the firewall, etc... you may install 3rd party software that you use instead of the native stuff. 3rd party software uses various installers, but you are almost always able to find that 3rd party software in add/remove programs when you want to get rid of it.

To me 'universal package management' is an oxymoron. You have package management for the managed software and other solutions for software you get elsewhere that may or may not all use the same installer, but optimally should all supply information to the native package management system on how to remove the stuff, and should not interfere with or replace the managed stuff. 

If it is packaged in a distribution independent way it doesn't really need a complicated solution whether it's an LSB compliant package or not, LSB compliance just give you a little more assurance that the software will work, won't conflict with the native stuff, will still work after you upgrade your distribution.

If it is packaged for your distribution and made available from an upstream web site, that doesn't mean there can't be some sanity in the packaging laid out by the LSB, like installing to '/opt/whatever/', having minimal dependencies, including it's own copy of things when newer stuff is desired that might conflict with the stuff supplied by the distribution vendor, etc...  

Later, Seeker

---

### Post by jetsam on 2010-05-22
Well, my last post unleashed a waterfall.  I'll have to read through those and get back to you.  

Perhaps there's something to it.

Maybe the users aren't responsible if the distros disagree.

---

### Post by ronacc on 2010-05-22
> **jetsam said:**
> Well, my last post unleashed a waterfall.  I'll have to read through those and get back to you.  



no but when we are in "wait mode" we'll chew over anything to reileve the boredom .

---

### Post by jetsam on 2010-05-22
Yeah it's easy to revel in boredom... 

It's pretty effing hard to process waste.  

What do you want?  Why aren't you getting it yourself?  Now!

---

### Post by seeker5528 on 2010-05-24
> **jetsam said:**
> Maybe the users aren't responsible if the distros disagree.

From the distribution vendor perspective, it's a question of support.

When you have a managed environment, releases are specific versions of various components at the base level, and that continues into the upper levels where things are compiled and tweaked specifically for those, bug fixes applied to fix issues specific to that particular combination of things that were included in the release. 

Every time something is changed, there is a QA process where you have to try to insure things continue to work together without new bugs or regressions being introduced. The bigger the change, the more likely it is that there will be unintended consequences.

Because of these issues, distributions are typically going to do one of three things.

[list]1: Have multiple supported releases at any given time where none of the provided software changes beyond what is required to take care of security issues.[/list]

[list]2: Have a single supported release, requiring you to upgrade to each new release if you want to keep up with new software and security updates.[/list]

[list]3: Have a rolling release, where what is considered a release in traditional terms is really just a snapshot of how things were at a given time and various things either individually or by groups of related things are always being rolled over to newer versions.[/list]

When it comes to open source and the up stream there are various levels of support depending on how the upstream project approaches things, the available developer manpower, and how much users get involved with helping each other. Sometimes other than users helping each other, the support from the developers may be none, only if you are compiling from source code, only if you are willing to compile the version that's in development from SVN, CVS, etc..., only if you are using the generically compiled and packaged version from our website or these specific packages for distribution X, Y, and Z.

So the main issues with that are that distribution vendors, unless you have a support contract where they get paid to provide a solution that fits your specific need, want to insulate themselves from having to support the additional problems that come from introducing new versions of stuff into their release pool of software. Upstream projects want to insulate themselves from having to deal with issues that were introduced by the individuals or groups that packaged the software for your distribution.

When it comes to commercial software the ISVs are often only going to want to support a single package that works with multiple distributions and versions of those distributions or provide packages that are supported for 2 or 3 different specific distributions, but are generic enough they will probably work on other distributions that use the same packaging format as one of the supported distributions and even when they do provide a generic binary they may only support it on 2 or 3 distributions.

In the context of what has been discussed in this thread I would guess that if this idea of having a list of PPAs in Software Center that can be enabled to get newer versions of some software is going to be supported there may want to be some guidelines along the lines of.....

[List]Packaged as generically as possible so that to the extent possible the same package will work on all versions of Ubuntu that are still currently supported.[/list]

[list]Install in '/opt/whatever/' so the repository and PPA versions can be installed at the same time without conflicts.[/list]

[list]If necessary use different configuration/data directories to avoid conflicts between the PPA and repository versions.[/list]

[list]Include it's own copy of things when there may be incompatible versions of those things in different supported Ubuntu releases.[/list]

[list]Have a way to identify the oldest release the software will work on so Software Center can determine this and dynamically provide the option to enable a PPA based on the release a user happens to be running.[/list]

If such a thing got the green light it might also provide the opportunity to urge the people working on these PPAs to try working with the upstream and Debian developers on getting a '/debian/' directory included in the source code directory that would be acceptable to Ubuntu, Debian, and Upstream devs alike. 

Later, Seeker

---

### Post by Scotty Bones on 2010-05-25
> **Longinus00 said:**
> Virtualbox does this because 3.1.6 to 3.1.8 is a bugfix release while 3.1.* to 3.2.* is a major release. You're less likely to have regressions upgrading from 3.1.6 > 3.1.8 than 3.1.* > 3.2 That's the whole point behind the versioning scheme. This is rather important information to sysadmins.
[http://en.wikipedia.org/wiki/Software_versions#Change_significance](http://en.wikipedia.org/wiki/Software_versions#Change_significance)


You are projecting. It **not a problem** because the average user doesn't care what he has installed, so long as it works. Look at the prevalence of old browsers/operating systems here [http://www.w3counter.com/globalstats.php](http://www.w3counter.com/globalstats.php) More page hits with ie 6 than with osx.

Umm...yeah. I do believe that updating from one major release to the next (not from point to point) is the main topic of discussion in this thread. Your first point is valid from a sysadmins perspective, in a corporate environment. SW should be tested throughly before deployment, regardless of whether it is a point or major upgrade. But I am not talking about business here, I'm talking about the average user. In the real world the one issue continually impressed upon the average user is the importance of keeping their SW up-to-date. Just ask any technician in the field what their most commonly given piece of advice is. In this respect I am not projecting but voicing a valid concern.

IE6...really! You do know that new versions of IE are pushed out through Windows Update automatically, right? If you are an average user running IE6, then you are most likely still running Win98 and I take pity on you. Which by the way, many corporations do still run Win98 in production environments in which their SW will not run on newer versions of windows or even newer versions of IE on newer OS's. Corporate SW compatibility (mostly SW written in house many years ago) is the major reason why IE6 is not completely dead yet. Not because the average user likes it or thinks it good enough.

---

### Post by Longinus00 on 2010-05-25
> **Scotty Bones said:**
> Umm...yeah. I do believe that updating from one major release to the next (not from point to point) is the main topic of discussion in this thread. Your first point is valid from a sysadmins perspective, in a corporate environment. SW should be tested throughly before deployment, regardless of whether it is a point or major upgrade. But I am not talking about business here, I'm talking about the average user. In the real world the one issue continually impressed upon the average user is the importance of keeping their SW up-to-date. Just ask any technician in the field what their most commonly given piece of advice is. In this respect I am not projecting but voicing a valid concern.

Keeping up to date is important in order to keep up with bugfixes. Because we are using open source software we can backport bugfixes into older versions. This is why you keep getting updates every once in awhile, even if you're over a year into a LTS release. Nowhere does that require newer versions of software.

> **Scotty Bones said:**
> 
IE6...really! You do know that new versions of IE are pushed out through Windows Update automatically, right? If you are an average user running IE6, then you are most likely still running Win98 and I take pity on you. Which by the way, many corporations do still run Win98 in production environments in which their SW will not run on newer versions of windows or even newer versions of IE on newer OS's. Corporate SW compatibility (mostly SW written in house many years ago) is the major reason why IE6 is not completely dead yet. Not because the average user likes it or thinks it good enough.

How does that explain the prevalence of IE 7 and firefox 3 (not 3.6) users?

---

### Post by ronacc on 2010-05-25
To many if not most people a computer is just a tool , not a treasured possession to be lovingly cared for and maintained . When is the lat time you updated your hammer or rake ?

---

### Post by LiquidMeson on 2010-05-26
keep in mind applications could add ppa upon install.

Example, when you install dropbox it adds itself to your sources list so that it gives you the latest version...

I see this as more of a application specific problem. 

If you install Firefox from Mozilla's website it should add itself to the sources list so it follows their releases. 

If it's installed from the software store it should follow Canonicals releases.

---

### Post by | MM | on 2010-05-26
Hopefully, there will be something like this available in software-center.

 Features planned (10.10):
   - New applications show up in the software center ("open the floodgates")

[https://blueprints.edge.launchpad.net/ubuntu/+spec/foundations-m-software-center-roadmap](https://blueprints.edge.launchpad.net/ubuntu/+spec/foundations-m-software-center-roadmap)

---

### Post by Speed_arg on 2010-05-26
Nice, at least they heard me about the extreme slowness USC has. Although, they planned fixing it for 11.04 :(

---

