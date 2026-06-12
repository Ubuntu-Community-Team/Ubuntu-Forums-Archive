---
title: "Systemd instead of Upstart?"
date: 2010-10-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by paul_in_london on 2010-10-13
I was reading about **systemd** recently:

[http://www.h-online.com/open/news/item/Systemd-presented-as-SysV-Init-and-Upstart-alternative-991875.html](http://www.h-online.com/open/news/item/Systemd-presented-as-SysV-Init-and-Upstart-alternative-991875.html)
[http://brainstorm.ubuntu.com/idea/24701/](http://brainstorm.ubuntu.com/idea/24701/)
[http://lwn.net/Articles/389149/](http://lwn.net/Articles/389149/)
[https://bbs.archlinux.org/viewtopic.php?pid=828523#p828523](https://bbs.archlinux.org/viewtopic.php?pid=828523#p828523)

Was just wondering if any of you guys have tried it. AFAIK there'll be a package for Debian, but not specifically for Ubuntu:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=580814](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=580814)

---

### Post by ranch hand on 2010-10-13
live-config-systemd
"This package contains the systemd backend (experimental!)."
Debian testing repo.

Only entry I can find.  Might all still be in the Debian experimental repos.  Most stuff there is pretty unstable much more than the Debian unstable repo.

---

### Post by autocrosser on 2010-10-13
Well--I think that Scott R is behind UpStart, so I would guess that systemd would be a very long if ever time coming to Ubuntu......

---

### Post by xebian on 2010-10-13
IIRC Fedora is sticking with upstart for now vs systemd even though systemd is RH development.

---

### Post by seeker5528 on 2010-10-13
> **paul_in_london said:**
> Was just wondering if any of you guys have tried it. AFAIK there'll be a package for Debian, but not specifically for Ubuntu:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=580814](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=580814)

Incentive to try it seems pretty low at this point.

It may be developed from a standpoint of avoiding some of the perceived problems with Upstart and other init systems, but by the time it gets to a point where it does better than Upstart, Upstart will have gotten better as well, so it may never reach a point where it is clearly better than Upstart. But it is good to have competition and, theoretically, developers of each can see elements from the other system that work and make improvements based on those. As long as they and any other alternatives maintain compatibility for sysv/LSB type init scripts for the 3rd party stuff, it shouldn't matter that much which is used within an any given distribution.

Later, Seeker

---

### Post by gnomeuser on 2010-10-14
Systemd is in so many respects far better designed than Upstart in the sense of optimizing for the right use cases and avoiding work.

I would love to see it in Ubuntu but I doubt that will happen as Canonical have spent a small fortune developing Upstart.

I think if this is to happen it will have to be driven by the community which is fine.

The most interesting feature from a user perspective is the boot time enhancements but these require patches to a number of daemons to handle sockets the way systemd expects. While we could likely take these from Fedora, it would still mean replacing a number of core packages with ppa versions during testing.

From an admin pov I think the control group management is far more interesting, this requires the kernel to have the cgroup stuff enabled, I don't know if we do this currently. If not that is another package we would have to change.

I think we can do it, and I would certainly be willing to invest time in such an effort.

What do you say to forming an Ubuntu Systemd team and getting started?

---

### Post by MishaAct on 2010-10-14
> **paul_in_london said:**
> I was reading about **systemd** recently:

[http://www.h-online.com/open/news/item/Systemd-presented-as-SysV-Init-and-Upstart-alternative-991875.html](http://www.h-online.com/open/news/item/Systemd-presented-as-SysV-Init-and-Upstart-alternative-991875.html)
[http://brainstorm.ubuntu.com/idea/24701/](http://brainstorm.ubuntu.com/idea/24701/)
[http://lwn.net/Articles/389149/](http://lwn.net/Articles/389149/)
[https://bbs.archlinux.org/viewtopic.php?pid=828523#p828523](https://bbs.archlinux.org/viewtopic.php?pid=828523#p828523)

Was just wondering if any of you guys have tried it. AFAIK there'll be a package for Debian, but not specifically for Ubuntu:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=580814](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=580814)
OMG
That one is pulseaudio and avahi developer
Avahi is ill-designed (reserving .local for internal needs is ever stupid idea), pulseaudio still feels unstable through years.
I wouldn't trust him such an important subsystem.
I would recommend anyone not to use it until it become reliable solution. But I highly doubt it will ))

---

### Post by vishalrao on 2010-10-14
I believe I saw a blueprint for NN titled "finish upstart" - meaning what? complete pending upstart changes - possibly improving boot speed further?

---

### Post by Reiger on 2010-10-14
> **gnomeuser said:**
> Systemd is in so many respects far better designed than Upstart in the sense of optimizing for the right use cases and avoiding work.

To some extent. From what I read in the introduction blog post, systemd is inherently a desktop subsystem which does not play well with server type daemons.

It's heart and soul is to start up stuff only when needed, and shut things down aggressively when no longer required. This is perfectly sensible thing to do for a laptop on batteries, but becomes decidedly less fun with services which you might use only occasionally but when you *do* use them you need them to be running *right then*. It's no use having a SSH connection time out over a local network because the SSH daemon is not running, and it's little use either to do a lot of development work on your personal website then intend to do some testing only to find out that Apache 2 is napping -- if nothing is listening connections will fail. And your performance is gone, too.

So for servers or server-type work it looks not that good. It could be the greatest thing since sliced bread but right now it looks more like croissant sopped in French coffee: theoretically the croissant is delicious but I have my doubts about the “soppy” and the “French” parts (lots of milk and not much coffee).

---

### Post by MacUntu on 2010-10-14
With the Upstart author's Apple affinity, I'm not sure if the system's flaws aren't there for a simple reason: to drive users to Mac OS X. Systemd's author on the other hand is also the author of PulseAudio, so its flaws should be more natural w/o any evil motives. I'm all pro systemd.

:lol:


**Edit:** If you didn't realize that I was just kidding, then please send me a PM so I can put you on my ignore list. #-o

---

### Post by 23meg on 2010-10-14
> **MishaAct]OMG
That one is pulseaudio and avahi developer[/QUOTE]

Nice ad hominem.

[QUOTE=MacUntu said:**
> With the Upstart author's Apple affinity, I'm not sure if the system's flaws aren't there for a simple reason: to drive users to Mac OS X. Systemd's author on the other hand is also the author of PulseAudio, so its flaws should be more naturally w/o any evil motives. I'm all pro systemd.

:lol:

Unless you make that smiley four times bigger or use some kind of "kidding" tag, there will soon be people seriously putting those forward as arguments parrot-fashion in favor of switching to systemd all over the web.

---

### Post by MacUntu on 2010-10-14
Fixed, but honestly: can it be more obvious that I was just kidding?

---

### Post by MishaAct on 2010-10-14
> **mgunes said:**
> Nice ad hominem.
I'm completely ombiassed, but I see only bad-designed projects of this guy. Every time I launch gnome I see avahi's message about .local domain and it can't do anything. On the other hand, I have sound issues at my job after week gnome uptime. They usually being resolved after logout-login. So, it's pure pulseaudio problem.

---

### Post by 23meg on 2010-10-14
> **MacUntu said:**
> Fixed, but honestly: can it be more obvious that I was just kidding?

When typing into a vBulletin message box, you can never be too careful.

---

### Post by gnomeuser on 2010-10-14
> **Reiger said:**
> To some extent. From what I read in the introduction blog post, systemd is inherently a desktop subsystem which does not play well with server type daemons.

It's heart and soul is to start up stuff only when needed, and shut things down aggressively when no longer required. This is perfectly sensible thing to do for a laptop on batteries, but becomes decidedly less fun with services which you might use only occasionally but when you *do* use them you need them to be running *right then*. It's no use having a SSH connection time out over a local network because the SSH daemon is not running, and it's little use either to do a lot of development work on your personal website then intend to do some testing only to find out that Apache 2 is napping -- if nothing is listening connections will fail. And your performance is gone, too.

So for servers or server-type work it looks not that good. It could be the greatest thing since sliced bread but right now it looks more like croissant sopped in French coffee: theoretically the croissant is delicious but I have my doubts about the “soppy” and the “French” parts (lots of milk and not much coffee).


That is true, and those are concerns for which systemd needs to tell a convincing story. Hard but not unsolvable.

With Fedora switching to systemd I would be very surprised if a plan didn't exist to handle these situations. Red Hat tend to be.. fairly dictatorial, when it comes to use cases they care about for RHEL in Fedora and let's face it, they are server people. I doubt they would have agreed to evaluate it for deployment without having considered these problems.

Generally Lennart is good at coming up with elegant solutions for hard problems so I am interested in seeing what his answer is going to be long term. It is clear from certain aspects of Systemd that he does care about administration at least.

That being said, Systemd is still early in development. For Natty I would be happy if we could at least demonstrate it running on Ubuntu.

---

### Post by Starks on 2010-10-14
Considering how long the transition from sysvinit to upstart was, systemd is at least 2 years off.

---

### Post by xebian on 2010-10-14
And Fedora 14 is shipping with the Ubuntu upstart instead of the RH/Fedora systemd.  Shows how much faith there is for systemd.

---

### Post by zekopeko on 2010-10-14
> **xebian said:**
> And Fedora 14 is shipping with the Ubuntu upstart instead of the RH/Fedora systemd.  Shows how much faith there is for systemd.

Systemd is still in its infancy while Upstart was developed during a course of years and is present in Ubuntu from 6.10.

I just hope this doesn't become another Pulseaudio fiasco. Pushing for inclusion in Fedora by default so early doesn't look good to me. So baby steps are preferable here IMO.

---

### Post by 23meg on 2010-10-14
> **xebian said:**
> And Fedora 14 is shipping with the Ubuntu upstart instead of the RH/Fedora systemd.  Shows how much faith there is for systemd.

No, it just shows where systemd stands right now. They fully intend to integrate it in F15.

---

### Post by xebian on 2010-10-14
> **mgunes said:**
> No, it just shows where systemd stands right now. They fully intend to integrate it in F15.

That was said then for F14.  AFAIK early F14 alphas came out with systemd.

---

### Post by 23meg on 2010-10-14
> **xebian said:**
> That was said then for F14.  AFAIK early F14 alphas came out with systemd.

So? If it was postponed to the next release, it means the FESCO and developers responsible still have faith in it; that's what I meant. Lots of feature plans get postponed all the time; it's the nature of the beast.

---

### Post by ssam on 2010-10-14
> **MishaAct said:**
> OMG
That one is pulseaudio and avahi developer
Avahi is ill-designed (reserving .local for internal needs is ever stupid idea)


zeroconf networking is great. avahi seems better than howl (which it replaced). isn't the .local domain part of the zeroconf spec? you can't blame the developer/implementation for following the spec.

> **MishaAct said:**
> 
pulseaudio still feels unstable through years.


pulseaudio lets you do lots of useful things that could not be done before. it has been stable on all my hardware for years.

though i don't think systemd should be default in ubuntu until it proves its stability and its benefits over upstart. so maybe wait another cycle.

---

### Post by MacUntu on 2010-10-15
So, who's nuts enough to try it? There's also some information on what you need to do before you can use it in another distribution:

```
Porting systemd To New Distributions

HOWTO:
        You need to make the follow changes to adapt systemd to your
        distribution:

        0) Make your distribution recognized via the autoconf checks
        in configure.ac. Grep for the word "fedora" (case
        insensitively) and you should be able to find the places where
        you need to add/change things.

        1) Patch src/hostname-setup.c so that systemd knows where to
        read your host name from. You might also want to update
        status_welcome() in util.c.

        2) Check the unit files in units/ if they match your
        distribution. Most likely you will have to make additions to
        units/*.m4 and create a copy of units/fedora/ with changes for
        your distribution.

        3) Adjust Makefile.am to register the unit files you added in
        step 2. Also you might need to update the m4 invocation in
        Makefile.am. Grep for the word "fedora" (case insensitively)
        and you should be able to find the places where you need to
        add/change things.

        4) Try it out. Play around with 'systemd --test --system' for
        a test run of systemd without booting. This will read the unit
        files and print the initial transaction it would execute
        during boot-up. This will also inform you about ordering loops
        and suchlike.
```

Sounds like a piece of cake. :P:lol::lol:

---

### Post by Nerd_bloke on 2010-10-15
Here's a bit of background on the politics. 
Couple of videos from the ubuntudevelopers youtube channel with keybuk (wearing the same fetching shirt) talking about Upstart and drifting onto SystemD:
[Maverick UDS Upstart QA:36m30s]("http://www.youtube.com/watch?v=ehs2Rl9WSQs#t=36m30s")
[Debconf 10 Upstart:36m40s]("http://www.youtube.com/watch?v=GNUFA_nK_VM#t=36m40s")

Seems to boil down to other distributions not wanting to loose acknowledgements with [Canonical's copyright assignment]("http://itmanagement.earthweb.com/osrc/article.php/3904526/Ubuntu-Canonical-Wallow-in-Muddy-Waters-with-Contributors-Agreements.htm"), with a bit of "you use Bazaar instead of git" as a figleaf from RedHat.

Shame as PackageKit suffered from NIH too.

---

### Post by zekopeko on 2010-10-15
> **Nerd_bloke said:**
> Shame as PackageKit suffered from NIH too.

What do you mean by this?

---

### Post by Nerd_bloke on 2010-10-15
> **zekopeko said:**
> What do you mean by this?

"not invented here" good practical example is [Bug 148084]("https://bugs.launchpad.net/bugs/148084"); Fedora have a nice solution in place using PackageKit

---

### Post by zekopeko on 2010-10-15
> **Nerd_bloke said:**
> "not invented here" good practical example is [Bug 148084]("https://bugs.launchpad.net/bugs/148084"); Fedora have a nice solution in place using PackageKit

Debian and Ubuntu not adopting Packagekit isn't a NIH syndrome but technical deficiencies on the side of Packagekit. 

For the past few Ubuntu releases there have been numerous Packagekit related blueprints but they always get deferred  because Packagekit doesn't do what Debian and Ubuntu need it to. Why would they replace a good frontend to dpkg with a solution that doesn't cover part of Debian/Ubuntu use cases?

---

### Post by MacUntu on 2010-10-15
Now isn't that cool, with systemd the boot is done after just six seconds!

[img]http://img.xrmb2.net/images/294773.png[/img]

:P

---

### Post by gnomeuser on 2010-10-15
> **zekopeko said:**
> Debian and Ubuntu not adopting Packagekit isn't a NIH syndrome but technical deficiencies on the side of Packagekit. 

For the past few Ubuntu releases there have been numerous Packagekit related blueprints but they always get deferred  because Packagekit doesn't do what Debian and Ubuntu need it to. Why would they replace a good frontend to dpkg with a solution that doesn't cover part of Debian/Ubuntu use cases?

Session API which is part of GNOME and deployed widely. It would be a huge boon.

The effort they put into their PackageKit clone could easily have added the functionality they requested to PackageKit. 

Yes that means they would still lack some queuing features but having one standard accepted API would far outweight this deficiency long term.

---

### Post by gnomeuser on 2010-10-15
> **MacUntu said:**
> Now isn't that cool, with systemd the boot is done after just six seconds!

:P

That is pretty nifty, I assume this is without the socket changes still?

---

### Post by MacUntu on 2010-10-15
> **gnomeuser said:**
> That is pretty nifty, I assume this is without the socket changes still?
Actually I had no idea what I was doing. Just git cloned the source, made a couple of changes so it would compile, and booted with 'init=/bin/systemd'. :P I really know too little to make this even close to work. I wonder if those '\x2d' in the root partition's UUID are ok.

---

### Post by Reiger on 2010-10-15
> **gnomeuser said:**
> The effort they put into their PackageKit clone could easily have added the functionality they requested to PackageKit.

True. Although Packagekit can hardly be considered an adequate replacement for people spoiled with the goodness that is APT/aptitude. It might work better on yum/rpm based systems, but last time (admittedly a long time) I tried it on Fedora it simply appeared to roll over and die on the first massive update thrown its way.

I still do not trust KPackagekit to do anything remotely more complex than a straightforward no-additional-dependencies update, for anything remotely complex I defer to aptitude. That's probably a bit of an unfair knee-jerk response, rooted in a bias from past burns; but as long as KPackagekit lets me apply an update first and only then starts to check whether there are additional dependencies, I am not going to trust it with the health of my OS and it should not be put before people that do not know to run aptitude instead.

---

### Post by MacUntu on 2010-10-15
It's maybe easier to start there (not tried it yet): [http://packages.debian.org/experimental/i386/systemd](http://packages.debian.org/experimental/i386/systemd)

---

### Post by seeker5528 on 2010-10-15
> **Nerd_bloke said:**
> "not invented here" good practical example is [Bug 148084]("https://bugs.launchpad.net/bugs/148084"); Fedora have a nice solution in place using PackageKit

Considering the codec installer, command not found, etc.. have been in use for quite some time and those are specific use cases where packagekit does well, how is that a practical example?

That's totally different head than using packagekit as the engine for your main package management software. Something it hasn't proved to be good at, judging by the failings of all the KDE/Gnome/GTK package managers that have been created so far. 

Later, Seeker

---

### Post by dext on 2010-10-15
> **xebian said:**
> And Fedora 14 is shipping with the Ubuntu upstart instead of the RH/Fedora systemd.  Shows how much faith there is for systemd.

look at Plymouth, its still a bit young an needs fixing yet even Ubuntu is using it.you can use systemd in F14 but i'd only recommend using it in F14 by advanced users.

---

### Post by Nerd_bloke on 2010-10-15
> **seeker5528 said:**
> Considering the codec installer, command not found, etc.. have been in use for quite some time and those are specific use cases where packagekit does well, how is that a practical example?

That's totally different head than using packagekit as the engine for your main package management software. Something it hasn't proved to be good at, judging by the failings of all the KDE/Gnome/GTK package managers that have been created so far. 

Later, Seeker

I was just saying that an upstream/cross-distro solution can't be used by Ubuntu... looks like i hit a nerve with a throwaway comment.
Didn't mean to hijack the thread with PackageKit.

Meanwhile no-one even mentions the points raised about SystemD in the video links, which was the reason i posted to begin with.

---

### Post by seeker5528 on 2010-10-15
> **Nerd_bloke said:**
> I was just saying that an upstream/cross-distro solution can't be used by Ubuntu... looks like i hit a nerve with a throwaway comment.

If you mean the 'WTF !?!?! Has there been some improvement and commitment from upstream to make it more capable/robust/useful for general package management that I don't know about? What's wrong with just using it for the types of limited use case tools that it seems to be designed for and excels at?' nerve, than I'd say you probably hit it. :P

Later, Seeker

---

### Post by andye on 2010-12-21
This is an old thread now, but in case anyone comes across it...

Unofficial systemd packages for Ubuntu are available here:
[https://launchpad.net/~andrew-edmunds/+archive/ppa](https://launchpad.net/~andrew-edmunds/+archive/ppa)

For further information, see this wiki page:
[https://wiki.ubuntu.com/systemd](https://wiki.ubuntu.com/systemd)

---

### Post by MacUntu on 2010-12-21
Thansk for the update. I will definitely give this a try. :)

---

### Post by dino99 on 2010-12-21
Thanks for the links and this nice wiki :)

will follow closely this project.

---

