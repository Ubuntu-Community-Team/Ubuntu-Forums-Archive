---
title: "Recent Shotwell without building it from scratch?"
date: 2011-01-17
forum: Multimedia Software
---

### Post by neanderslob on 2011-01-17
Hi all, I'm running 10.04 after getting along notsowell with 10.10 however this gives me access to Shotwell 0.7.2 in the repos.  Is there any way I can get a more recent version of that program in 10.04 without building it from scratch?

---

### Post by mc4man on 2011-01-17
I don't know if there are any ppa's with the exception of one I've seen.
This is an interesting ppa to say the least and not having a lucid install can't say what impact it would have or the best way to use
(ie. - can you use it just for a specific package upgrade or should it be used more extensively.

It's called [Lucid quasi-rolling :) ]("https://launchpad.net/~guido-iodice/+archive/guiodiclucid")and has a ton of current packages for lucid - close to 500

It may be possible to add the ppa, update your sources (sudo apt-get update) and then just upgrade shotwell. After that you could disable the ppa so as not to upgrade additional stuff (unless you wanted to.
Again I can't say this is a good deal or not without trying myself - maybe later this week I'll do a lucid install somewhere and see what it offers, good and or bad.

---

### Post by neanderslob on 2011-01-17
Hehehehe Quasi-rolling eh?  Sounds glitchy and destructive; I'm so in! :D Don't worry about subjecting yourself to it if you don't have to; I'll let you know how my experience goes once I revive my computer.  :guitar:

---

### Post by lykeion on 2011-01-17
Above mentioned PPA does not seem to have shotwell-0.8 for Lucid. Also it'll not be added to the yorba PPA (Shotwell's PPA), see here: [http://www.mail-archive.com/shotwell@lists.yorba.org/msg00867.html](http://www.mail-archive.com/shotwell@lists.yorba.org/msg00867.html)

I wouldn't agree with it being easy to compile shotwell-0.8 in Lucid as it said in the mail-archive post. I'm on Lucid as well and spent the last half hour trying to compile it without succeeding. My best advice if you're desperate for shotwell-0.8 is to upgrade to Maverick.

---

### Post by neanderslob on 2011-01-17
Or you could just send me a .deb file when you're done because, well, you don't strike me as a quitter am I right?  Am I right?  ;)  No really though, given that shotwell is now default on ubuntu releases, it's somewhat surprising to me that it still seems to still be in relative obscurity on the web.  If the mood strikes me, I'll try the ol' gather the heaping pile of dependencies and compile it but I think I should just let it go before I blow too much time on it.  The upgrade to 10.10 probably is the easiest route.

---

### Post by mc4man on 2011-01-17
> Above mentioned PPA does not seem to have shotwell-0.8 for Lucid. 
No, it does - downloaded it to ck. the control file - see screen
(it's named for maverick but released for lucid

---

### Post by mc4man on 2011-01-17
Well went ahead w/ a lucid install (usb is quite fast

Installed just nvidia-current, then added the ppa.
shotwell 0.8.1 is easily installed, was just a few added/upgraded packages - works fine
> Upgraded the following packages:
libsqlite3-0 (3.6.22-1) to 3.7.4-1~ppa0

Installed the following packages:
exiv2 (0.19-1)
libexiv2-6 (0.19-1)
libgee2 (0.5.2-1~llvala1)
libgexiv2-0 (0.2.2-0lucid1)
libraw-dev (0.9.0-0ubuntu1)
shotwell (0.8.1-1~maverick1)
sqlite3 (3.7.4-1~ppa0)

Then did a full dist-upgrade, many packages were upgraded - all worked quite fine so far.
The ppa has 480+, 1350 individual available
From a multimedia viewpoint there the new current releases of totem, rhythmbox, banshee, vlc, mplayer, gstreamer plugins ect., ect.
While in some cases even newer, better are available for the most part not bad 
(for instance vlc 1.2 which must be built and mplayer which can be built or gotten from the mplayer daily ppa

The ppa doesn't replace your ffmpeg shared libs which for the most part is a good thing.

If I was running lucid I'd definitely use this, quite a timesaving over doing yourself

( when I used to use hardy, which was outdated on release, I set up a local repo and must of built, re-built and added around 170 packages to get it more up to date. Took days of work, so this ppa is quite interesting...

Also note that many of the package contributors of the ppa are well regarded

---

### Post by neanderslob on 2011-01-17
Hey thanks man.  So is it the case that shotwell is actually in the repo or did you compile it with all the upgraded packages?

---

### Post by mc4man on 2011-01-17
> So is it the case that shotwell is actually in the repo
It's in the repo - see screen in post 6

you can just add the ppa, run sudo apt-get update and then update your current shotwell to the 0.8.1 version, use synaptic.

You can also upgrade any other packages individually if available.

To see what's available from the ppa - open synaptic, click on the 'origin' tab and highlight the ppa. On right will show.

After that either go into software sources and disable the ppa or, if inclined, leave it enabled.
Though in the case of rhythmbox/rhythmbox-plugins the builds could be fixed

See screen for what about 'origins', ect.

Edit: After fooling around a bit I probably wouldn't use it to upgrade all - there are some packages that aren't fully enabled - rhythmbox- plugins is an example there. Better to pick and choose - then if not suitable easily reverted

---

### Post by Remix_88 on 2011-03-17
I wanted Shotwell for Lucid too, so I've created a PPA for it :-)

[LIST]
[*][https://launchpad.net/~flexiondotorg/+archive/shotwell](https://launchpad.net/~flexiondotorg/+archive/shotwell)
[/LIST]

My PPA contains Shotwell 0.8.1 built for Ubuntu Lucid 10.04 LTS. I created the PPA because I run Lucid at home and wanted the new version of Shotwell. Sadly, Yorba aren't going to provide a Lucid build of Shotwell 0.8.1 due to the reasons discussed in the following ticket:

[LIST]
[*][http://trac.yorba.org/ticket/3015](http://trac.yorba.org/ticket/3015)
[/LIST]

As mentioned in the ticket above, there are versions of Shotwell 0.8.1 available for Lucid in other PPAs. However, those PPAs contain hundreds of packages. If you're not that brave, like me, then hopefully my PPA provides what you need. I have built Shotwell 0.8.1 with minimal changes from the original Yorba source packages and not polluted my PPA with any unnecessary packages ;-) 

NOTE! My PPA has dependencies that are satisfied by the Yorba PPA, so you must also enable the Yorba PPA too.

[LIST]
[*][https://launchpad.net/~yorba/+archive/ppa](https://launchpad.net/~yorba/+archive/ppa)
[/LIST]

To install Shotwell 0.8.1 on Lucid do the following:

```
sudo apt-add-repository ppa:yorba/ppa
sudo apt-add-repository ppa:flexiondotorg/shotwell
sudo apt-get update
sudo apt-get install shotwell
```

---

### Post by Yettie on 2011-03-21
> **Remix_88 said:**
> I wanted Shotwell for Lucid too, so I've created a PPA for it :-)

Thanks so much for this. I've now installed it on my system and it seems to be working fine. =D>

---

