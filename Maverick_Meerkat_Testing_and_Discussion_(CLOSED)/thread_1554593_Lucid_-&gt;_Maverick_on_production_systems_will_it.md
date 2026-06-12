---
title: "Lucid -&gt; Maverick on production systems: will it be worth it?"
date: 2010-08-16
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by recluce on 2010-08-16
I have been running Maverick on a test system since Alpha 1. I will state that it works reasonably well for an alpha version and that this indicates a reasonably bug-free final version. So far, so good.

However, will it be worth the effort to update **production** systems from Lucid to Maverick? For server systems, unless they currently have an issue, my answer would be a definite NO, especially given the shorter life-span of Maverick (04/12) compared to Lucid (04/15).

For desktops and notebooks, I am a bit at a loss, so I am asking the opinion of you guys. What would be new/improved features that make it worth the effort to update in October? And please, tangible benefits, not just higher version numbers... ;)

---

### Post by VMC on 2010-08-16
It's going to be a wait and see. Its just not higher numbered kernels or programs but also more cutting edge software. That doesn't necessarily mean less stable, but possibly more refined.

Take for example xorg. There's a new one(1.9)coming along that should make booting faster, and I hope better.

It all depends on what you doing, what your after, type of work being done. I can't think of any previous Ubuntu releases that work any better than the current Lucid. And being an LTS it keeps getting more mature.

A topic at Kubuntu came up. Someone wanted to keep using Hardy and was worried about its future support. He was very happy using Hardy and didn't want or have any reason to upgrade.

I'm thinking some people just don't like the 6 month release schedule. Well that's just the beginning. It is after all supported for a long time after giving birth. :)

Right now I'm very satisfied with using Lucid, but also see some great things coming up with Maverick.

---

### Post by cariboo on 2010-08-17
Personally if I was running production systems, I'd stay with Lucid, unless there is a compelling reason to run the latest and greatest. Productions system should be stable, in many cases new versions != stable.

---

### Post by philinux on 2010-08-17
> **recluce said:**
> I have been running Maverick on a test system since Alpha 1. I will state that it works reasonably well for an alpha version and that this indicates a reasonably bug-free final version. So far, so good.

However, will it be worth the effort to update **production** systems from Lucid to Maverick? For server systems, unless they currently have an issue, my answer would be a definite NO, especially given the shorter life-span of Maverick (04/12) compared to Lucid (04/15).

For desktops and notebooks, I am a bit at a loss, so I am asking the opinion of you guys. What would be new/improved features that make it worth the effort to update in October? And please, tangible benefits, not just higher version numbers... ;)

+1 for cariboos post.

---

### Post by ktp on 2010-08-17
> **cariboo907 said:**
> personally if i was running production systems, i'd stay with lucid, unless there is a compelling reason to run the latest and greatest. Productions system should be stable, in many cases new versions != stable.

+1

---

### Post by teh603 on 2010-08-18
For laptops with Intel i-series processors (i3, i5, i7), its worth trying. In Lucid, those systems should resume from suspend or hibernate to a blank screen due to the SCI_EN bug which should have been patched already but hasn't. Maverick fixes that bug without needing a PPA.

I would think that being able to suspend/hibernate and resume without a black screen of death would be a compelling reason.

---

### Post by x-shaney-x on 2010-08-18
I have a laptop with an i3 processor running lucid and have no problems with suspend/hibernate/resume at all.

---

### Post by hugmenot on 2010-08-19
> **x-shaney-x said:**
> I have a laptop with an i3 processor running lucid and have no problems with suspend/hibernate/resume at all.

That&#8217;s because your kernel isn&#8217;t [sentient]("http://www.chipx86.com/blog/2010/08/17/sentience-discovered-in-the-linux-kernel").

---

### Post by Neezer on 2010-08-19
the 10.10 kernel will have TRIM support for SSD's because it will have kernel version higher than 2.6.33.

That is enough for me...I have upgraded my kernel, but it is my understanding that I won't get upgrades for my new kernel because it isn't in the 10.04 repos....

Please correct me if I'm wrong on this.

---

### Post by Denis Krajnc on 2010-08-19
I think that decision is up to you. For production systems I think it's best to stay with LTS versions, so you don't have to install every six months. But for everyday use computers is best to make a clean install every six months to a newest version.

---

### Post by KdotJ on 2010-08-19
"if it ain't broke don't fix it" as they say...

---

### Post by teh603 on 2010-08-19
> **Denis Krajnc said:**
> I think that decision is up to you. For production systems I think it's best to stay with LTS versions, so you don't have to install every six months. But for everyday use computers is best to make a clean install every six months to a newest version.Every six months? The lifespan of an Ubuntu release is a year and a half, not six months. I was still using Jaunty right up until its expiration date a few months ago.

Course, that was mostly because Karmic was sch a pain in the butt and had some really nasty regressions...

---

### Post by cascade9 on 2010-08-19
> **cariboo907 said:**
> Personally if I was running production systems, I'd stay with Lucid, unless there is a compelling reason to run the latest and greatest. Productions system should be stable, in many cases new versions != stable.
 
 +1. Moving from an LTS release to a 'normal' ubuntu release for production machines doesnt seem like the best idea to me. 

Also, newer versions can have, well, support issues the last version didnt have. Example? 10.04 will not ever support nvidia cards that need driver 71.xx.xx- the 71.xx drivers are never going to be released in a version that will work with xorg 1.8. 

> **VMC said:**
> Take for example xorg. There's a new one(1.9)coming along that should make booting faster, and I hope better.

I wonder what that is going to break...... 

> **teh603 said:**
> Every six months? The lifespan of an Ubuntu release is a year and a half, not six months. I was still using Jaunty right up until its expiration date a few months ago.


Umm...unless I've made some silly mistake, 9.04 is supported up till october, 2010. 

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Denis Krajnc on 2010-08-19
Yes, but new release of Ubuntu is every six months.

---

### Post by ranch hand on 2010-08-19
> **Denis Krajnc said:**
> Yes, but new release of Ubuntu is every six months.
If that release is not an LTS, it is very similar to the Alpha and Beta snapshot releases.  It is a stepping stone to the next LTS.  No no one needs to install them.

That said, they are FUN.

There is an LTS release every 2 years, with 3 years of support, those are the ones to watch.

If you have a production box, I would stick with the LTS.  I admit to rarely using it but my secure business OS is still 8.04.  Solid as a rock (and boring).

---

### Post by nanog on 2010-08-19
>  But for everyday use computers is best to make a clean install every six months to a newest version.

IMO, its much easier and safer to upgrade an existing ubuntu. A fresh install can leave you without a working kernel, driver, or with a dead or buggy installer.  

In fact, when I get a new box I never install a fresh copy of ubuntu. I just drop a dd image from an existing install. Edit fstab and install drivers -- boom -- working system with everything tweaked and configured.

---

### Post by Thomas Garman on 2010-08-20
I feel like I am on this constant upgrade treadmill which is always requiring a download of 100 MB that end up to add nothing whatsoever to my end-user experience.  There isn't anything I do with 10.04 that I wasn't already doing with 9.10 and even though I am testing 10.10 Alpha 3 on a Netbook I am really not seeing why anyone would bother.
 
The developers seem to have bet the farm on the buzz that will be generated by Gwibber.
 
I couldn't care less about Gwibber.
 
There really is no reason to upgrade at all if your computer works fine the way it is.

---

### Post by ranch hand on 2010-08-20
I am not sure why you are so cranky but here are a few things to consider.

9.10 testing was a bugger, a real rough ride.  This was to get a lot of new stuff in so that it could go in 10.04.

10.04 is an LTS.  These are conservative releases.  They are not meant to be inovative.

If you are talking about 10.10 when mentioning the downloads then it is hard to respond.  User experience?  This is a build in progress.  There are no users.  There are testers.

Part of the tester experience is large downloads.  This is how a build progress'.

I really think you should get the knot out or your knickers.

---

### Post by phillw on 2010-08-20
> **ranch hand said:**
> +1

Stay with LTS unless you really need the latest all singing (some times off tune) all dancing (it may tread on your toes) versions.

If you'd like to have a 'play' with the newer ones, do as I and many others do; make a few partitions up and pop them on there. If you rsync your exisxting /home partition to their 'local' home area, your 'real' data will be safe no matter what happens to your 'play' area. As releases move to the beta level, I start to use them as production, but then keep a /spare_home partition rsynced up with the beta area and my 'production' work stored on external servers. To easier explain, for the 10.04  alpha release cycle I had
/9.10
/home_9.10
/10.04
/home_10.04

At the beta, it became
/9.10
/home_9.10
/10.04
/home_10.04
/Spare_home_10.04

You can never have too many backups of your data, my LAMP server stuff is stored on an external server, this means if absolute disaster occurred to me, I have enough backups of /home and my LAMP stuff to do a rebuild.

That may seem very involved, but it is a testing area. As 10.04 got to RC, with it and lubuntu I was up to sda12; which I know is tiny as per what ranch-hand gets up to :-)

Regards,

Phill.

---

### Post by Asmodai on 2010-08-20
Apparently, in 2.6.35 improvements to the CPUFreq governor were made.
Until now, this has been a problem in Karmic (and probably Lucid), because resource-hungry games stutter in "ondemand" mode. To get a steady frame rate, you have to switch to "performance" mode manually.
So I believe this will work much better in Maverick.

---

### Post by cariboo on 2010-08-20
People that run production systems, don't usually play games, as they use their computers to get work done. So that argument doesn't work.

---

### Post by recluce on 2010-08-21
As I mentioned in the first post of this thread, I am not talking about systems that have issues with Lucid, for them the story is obviously different. The summary below is for systems that run fine on Lucid.

So from the discussion as it stands now:

Server Systems: NO, stay with Lucid (LTS !!!)

Desktops / Notebooks: upgrade to Maverick if you have SSDs with Trim support

---

### Post by cariboo on 2010-08-21
When Lucid came out, there were quit a few people that had problems the day it was released, so I would suggest waiting for the first point release before installing on a production server.

For the release notes, have a look here:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes/ChangeSummary/10.04.1](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes/ChangeSummary/10.04.1)

---

### Post by Queue29 on 2010-08-21
> 10.04 is an LTS. These are conservative releases. They are not meant to be inovative.

I lol'd. If an LTS is supposed to be stable or non-innovative, 10.04 LTS definitely broke some rules.

---

### Post by antiram on 2010-08-23
there is a kernel ppa with maverick 2.6.35.x kernel for lucid, if someone needs ssd trim support.
[https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

it updates automatically to new versions

---

### Post by teh603 on 2010-08-23
> **ranch hand said:**
> I am not sure why you are so cranky but here are a few things to consider.

9.10 testing was a bugger, a real rough ride.  This was to get a lot of new stuff in so that it could go in 10.04.

10.04 is an LTS.  These are conservative releases.  They are not meant to be inovative.

If you are talking about 10.10 when mentioning the downloads then it is hard to respond.  User experience?  This is a build in progress.  There are no users.  There are testers.

Part of the tester experience is large downloads.  This is how a build progress'.

I really think you should get the knot out or your knickers.I dunno. I'm using Maverick and haven't found many bugs worth reporting. The odd one with Plymouth... but that's Plymouth and my own thoughts on Ubuntu and Plymouth were vented in the 10.04 testing cycle.

Although I do agree with the part on large downloads. I think I burned 20 DVD-Rs through the entire test cycle for 10.04. Didn't find many bugs, though. For an "unstable" release, Lucid and Maverick have both been rock solid.

> **Queue29 said:**
> I lol'd. If an LTS is supposed to be stable or non-innovative, 10.04 LTS definitely broke some rules.Yeah, I was under the impression that they're meant to just be supported for more than a year and a half or so, to allow corporations some level of consistency.

---

### Post by 23meg on 2010-08-24
It's hard to give meaningful advice without knowing hardware specifics of those "production systems", what is to be produced on them, and in what kind of scenario.

Long term support is usually a plus, but not always, and can be outweighed by other factors, thus "production systems should always use/prefer LTS releases" is too general an advice to be useful.

---

### Post by Nick_Jinn on 2010-08-24
Multi-touch support is a big deal in the new release. Thats reason enough for me.

---

