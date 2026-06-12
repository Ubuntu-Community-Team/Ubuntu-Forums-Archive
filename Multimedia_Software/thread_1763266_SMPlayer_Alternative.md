---
title: "SMPlayer Alternative"
date: 2011-05-20
forum: Multimedia Software
---

### Post by SushiAddiction on 2011-05-20
Hi
I'm looking for an SMPlayer Alternative. 

I play many mkv files that are usually h264 aac ssa subs

I need a player that will;
1) keep a playlist when you close and then open the program
2) Allow you automatically select preferred Audio/sub with preference
  e.g. Audio - jpn,any  Subs - jpn,eng,any
3) Allows you to show filename in the playlist... and does not automatically show the title instead I HATE THIS

I've tried VLC but it does not satisfy condition 1 
Totem does satisfy condition 2 & 3

xine & GnomeMPlayer do not work at all with these files.
I've watched thousands of these on win and linux.
I'm a little disappointed with all other linux players compared to smplayer    

Thanks for any help

EDIT> VLC uses Media Library instead of playlist to keep files.
I would prefer SMPlayer but beggars can't be choosers.

EDIT2 >>> seems the problem [some h264 files] is not with SMPlayer but MPlayer 1.0rc4. Will have to wait for mplayer update. SMPlayer rulz

---

### Post by beew on 2011-05-20
Umplayer?
[URL="http://www.webupd8.org/2011/04/umplayer-available-in-webupd8-ubuntu.html"]
http://www.webupd8.org/2011/04/umplayer-available-in-webupd8-ubuntu.html[/URL]

---

### Post by ron999 on 2011-05-20
> **SushiAddiction said:**
> 

EDIT2 >>> seems the problem [some h264 files] is not with SMPlayer but MPlayer 1.0rc4. Will have to wait for mplayer update. SMPlayer rulz

Hi
There's a tutorial to compile mPlayer from SVN here:-[http://ubuntuforums.org/showthread.php?t=1542240]("http://ubuntuforums.org/showthread.php?t=1542240")

---

### Post by beew on 2011-05-20
You can get up to date builds for mplayer fom ppas.

I use this one [https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc")
I don't use coreavc but the mpalyer  is excellent, it is built from svn and is updated frequently.

Another one is [https://launchpad.net/~motumedia/+archive/mplayer-daily]("https://launchpad.net/%7Emotumedia/+archive/mplayer-daily")
Most people recommend this though I find the first one more stable on my machines.

Umplayer is a fork for Smplayer (both use mplayer as their backend) but it has more options.

---

### Post by SeijiSensei on 2011-05-20
If you're not afraid of compiling your own software from source, you could give [mplayer2](http://www.mplayer2.org/) a try.  Download the source code from [here]("http://ftp.mplayer2.org/pub/release/mplayer2-build-2.0.tar.bz2") then run the following:

```

sudo apt-get install build-essential autoconf automake libtool yasm
sudo apt-get build-dep mplayer
cd /path/to/directory/with/downloaded/source
tar xjvf mplayer2-build-2.0.tar.bz2 
cd mplayer2-build-2.0
make -j 6
make
make install

```

(You'll see a bunch of warnings from the compiler that you can ignore.)

You'll now have a new mplayer binary in /usr/local/bin.  In smplayer, navigate to Options > Preferences > General and replace "mplayer" with "/usr/local/bin/mplayer" in the "MPlayer executable" box.  Click OK, then try and play a file that's been giving you problems.

---

### Post by SushiAddiction on 2011-05-20
Thanks for all the answers everyone. I've only been using ubuntu for 3 months now so I think I'll go with the first option below. I have to learn more before I start compiling.

> **beew said:**
> You can get up to date builds for mplayer fom ppas.

I use this one [https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc")
I don't use coreavc but the mpalyer  is excellent, it is built from svn and is updated frequently.

Another one is [https://launchpad.net/~motumedia/+archive/mplayer-daily]("https://launchpad.net/%7Emotumedia/+archive/mplayer-daily")
Most people recommend this though I find the first one more stable on my machines.

Umplayer is a fork for Smplayer (both use mplayer as their backend) but it has more options.

I'm guessing if I want to change back to synaptic, I uninstall delete above PPA and then install from synaptic. It probably works the same way when you build it from source but there are more things to learn/go wrong :D I'm inexperienced :D

---

### Post by beew on 2011-05-20
> **SushiAddiction said:**
> Thanks for all the answers everyone. I've only been using ubuntu for 3 months now so I think I'll go with the first option below. I have to learn more before I start compiling.



I'm guessing if I want to change back to synaptic, I uninstall delete above PPA and then install from synaptic. It probably works the same way when you build it from source but there are more things to learn/go wrong :D I'm inexperienced :D

Adding a ppa will integrate it into Synaptic, so after you add the source (open Synaptic, go to Settings > repositories > Other software and add the ppa and reload Synaptic) you will be prompted to update mplayer and it will fetch it from the ppa instead of Ubuntu's official repo. 

The advantage of ppa over installing from source is that (apart from it takes less work and knowledge) you get update automatically through Synaptic or update manager whereas if you install from source you have to do it manually and recompile everytime you want a newer version (and likely run into dependencies problems). Installing from source is educational but if you just want things to work ppa would be the recommended route.

If in case something is broken you can uncheck the box for the ppa in Synaptic and reload, then uninstall mplayer and reinstall it, since the ppa is unchecked it will reinstall the version from the Ubuntu repo (or, you can add a different ppa before you reinstall then it will install from the new ppa, Synaptic always installs the latest version available in your repositories,--that include the Ubuntu repos and all the ppas you have addded)

Another option for reverting would be to use a command line utility called ppa-purge (the gui version in Ubuntu tweak doesn't work apparently) But  since there are only one or two packages for mplayer you don't really need this.

P.S. mplayer (and everything for that matter) does not get updated in the Ubuntu reposoitories  because the official repos are frozen for the whole life time of the release (18 months +)  except for security updates , so there will be no new feature/bug fixes in the Ubuntu version after release (except for the few programs in the backport and Canonical recommended repos). It has nothing to do with the developer being too busy. It is a major drawback of Ubuntu IMO. That's why I use a lot of ppas to keep my software up to date.

---

### Post by jmore9 on 2011-05-20
Dragon Player

Kaffeine

kplayer

Are three others that come to mind

---

### Post by andrew.46 on 2011-05-20
I am looking around for an SMPlayer replacement as well, the UMPlayer subversion repository seems broken at the moment though. Is it working for anybody? The command I am using is:

```

svn co https://umplayer.svn.sourceforge.net/svnroot/umplayer/umplayer/trunk umplayer

```

---

### Post by mc4man on 2011-05-20
> **andrew.46 said:**
> I am looking around for an SMPlayer replacement as well, the UMPlayer subversion repository seems broken at the moment though. Is it working for anybody? The command I am using is:

```

svn co https://umplayer.svn.sourceforge.net/svnroot/umplayer/umplayer/trunk umplayer

```
Try again - seems fine now...

---

### Post by andrew.46 on 2011-05-20
> **mc4man said:**
> Try again - seems fine now...

Indeed it does :). I note most of the docs in the source point to smplayer!

---

### Post by mc4man on 2011-05-20
> **andrew.46 said:**
> Indeed it does :). I note most of the docs in the source point to smplayer!
Taking a quick glance inside it looks like it is smplayer + some add. <?whatever?>
Take a look at changelog, the debian-rvm, ect. ect.

[http://sourceforge.net/projects/umplayer/forums/forum/1086463/topic/4452141](http://sourceforge.net/projects/umplayer/forums/forum/1086463/topic/4452141)

---

### Post by andrew.46 on 2011-05-20
Looks quite interesting after I cobbled a build together on my 'other' distro. I particularly like the youtube viewer and I have attached a screenshot of this in action for anybody interested. I am contemplating adding this to my MPlayer guide just for something completely different :).

**Edit: **Very nice shoutcast client as well!

---

### Post by mc4man on 2011-05-21
> **andrew.46 said:**
> Looks quite interesting after I cobbled a build together on my 'other' distro. I particularly like the youtube viewer and I have attached a screenshot of this in action for anybody interested. I am contemplating adding this to my MPlayer guide just for something completely different :).

**Edit: **Very nice shoutcast client as well!
Not sure how you built in slack - here in 11.04 the makefile inside "trunk" wouldn't work (too high a qt-designer version in 11.04
But from the trunk prompt this worked well to build 2 .deb's
```
./create_deb.sh
```

(an apt-get of smplayer's build-dep's would suffice

---

### Post by nothingspecial on 2011-05-21
> **andrew.46 said:**
>  I am contemplating adding this to my MPlayer guide just for something completely different :).



Please do :)

off topic

@ Andrew.

If you don't mind, will you link your sox guide to your wiki page please.

Thanks

---

### Post by andrew.46 on 2011-05-21
> **nothingspecial said:**
> If you don't mind, will you link your sox guide to your wiki page please.

Is that the little one that enables mp3 encoding with sox?

---

### Post by nothingspecial on 2011-05-21
> **andrew.46 said:**
> Is that the little one that enables mp3 encoding with sox?

Yep

---

### Post by andrew.46 on 2011-05-21
> **nothingspecial said:**
> Yep

Done :).

---

### Post by nothingspecial on 2011-05-21
> **andrew.46 said:**
> Done :).

Thanks :D

---

### Post by andrew.46 on 2011-05-27
> **mc4man said:**
> Not sure how you built in slack - here in 11.04 the makefile inside "trunk" wouldn't work (too high a qt-designer version in 11.04
But from the trunk prompt this worked well to build 2 .deb's
```
./create_deb.sh
```

Finally had a little time to have a proper look at this and I have added UMPlayer instructions in the usual place:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

I had no trouble with qt-designer version though, have I done something differently to your own build? Just need to tighten up the pkgversion syntax a little but it is workable as is...

---

### Post by shantiq on 2011-05-28
> **beew said:**
> Umplayer?
[URL="http://www.webupd8.org/2011/04/umplayer-available-in-webupd8-ubuntu.html"]
http://www.webupd8.org/2011/04/umplayer-available-in-webupd8-ubuntu.html[/URL]



beew thanx for that one looks like a winner:KS

---

### Post by andrew.46 on 2011-05-28
> **shantiq said:**
> beew thanx for that one looks like a winner:KS

But PPAs are no fun :).

---

### Post by shantiq on 2011-05-28
well andrew for dorks like me they are useful:KS i tried the svn and it installed fine but once on my machine i do not know how to start the program it does not appear in applications so what is one to do?



that is why i plumped for the easy ppa route


so please how do you find/ start your svn once in your home folder/?


thanx    shan

---

### Post by andrew.46 on 2011-05-28
> **shantiq said:**
> well andrew for dorks like me they are useful:KS i tried the svn and it installed fine but once on my machine i do not know how to start the program it does not appear in applications so what is one to do?

Hey I was only half-kidding about the PPA thing :). I am not that familiar with the whole Unity thing but I found the svn UMPlayer by searching for it and then fixing it to the Unity side menu. But stay with the PPA UMPlayer and enjoy a great program! I am still blown away by the great youtube browser and I have been playing my secret vice (Rammstein) at full volume...

---

### Post by shantiq on 2011-05-28
> **andrew.46 said:**
> Hey I was only half-kidding about the PPA thing :). I am not that familiar with the whole Unity thing but I found the svn UMPlayer by searching for it and then fixing it to the Unity side menu. But stay with the PPA UMPlayer and enjoy a great program! I am still blown away by the great youtube browser and I have been playing my secret vice (Rammstein) at full volume...


Bloody Hell it is amazing Andrew :KS:KS and you can save/download the vid too

 BIG improvement on smplayer

---

### Post by andrew.46 on 2011-05-28
> **shantiq said:**
> BIG improvement on smplayer

It looks very nice! Not sure if rvm is caught up with real life, it has been over a year since the last SMPlayer release. I would be sorry to see a fine program like SMPlayer, which has been very useful to me over the years, slide into disuse...

---

### Post by mc4man on 2011-05-28
What I see here on a couple of installs is it (umplayer) works fine with online video, youtube ect. but goes south with local files,  - maybe just here, maybe not. (seems to play them, audio or video, but no controls, 1 thread at 100%, ect.
(will have to try on install where nothing's been modified later

---

### Post by shantiq on 2011-05-28
yes well quite mc4man

problems here too

will not stay full screen moves to the center like 50% and refuses to go properly full screen

so great on the youtube function but problems:KS:KS

---

### Post by beew on 2011-05-28
I have no problem playing local files or going on Youtube. I have installed Umplayer on Maverick and Natty and have used it on several different machines.

I installed from the webupd8 ppa instead of building it myself (so shame on me :))

@shantiq

The full screen problem may have to do with Compiz. I solved the problem by changing the launcher command to

```
env XLIB_SKIP_ARGB_VISUALS=1 umplayer %f
```

I had to do that with Smplayer too.

---

### Post by shantiq on 2011-05-28
thanx beew but it does not fix it i still get see attached

i can move it to 16:9 or 14:9 but when i double-click it reverts to

this small size   great player otherwise:KS

---

### Post by beew on 2011-05-28
Strange, I have no problem going full screen, or going from full screen to normal size and back during playback. This maybe a stupid question but have you tried other videos?

EDITED: I misunderstood your question before, the fix is for transparent screen with only a small area showing the video in the middle.

---

### Post by shantiq on 2011-05-28
ok good tip works (der Shan could have thought of trying that mayhaps):KS:KS:KS why would that one not work is still a mystery but thanx

---

### Post by beew on 2011-05-28
Yeah I guess it has something to do with the way the video is encoded, I have one video clip that VLC would play but Smplayer just wouldn't, but it plays fine when I changed vo from vdpau to xv.

---

### Post by mc4man on 2011-05-28
Figured out what was the problem here w/ local files ( not the actual cause yet..
Because i' trying some changes to unity and do a fresh install quite often have been installing mplayer from the mplayer daily ppa vs. building.
Apparently, at least on this hardware, umplayer has some issue with local files and the ppa's source/build
I think it may have something to do with caching.
screen 1 shows trying to play a .flac - controls are inactive, umplayer is frozen, cpu use is off to the races, but the flac plays.

Installing the 11.04 mplayer and all is fine - screen 2
I guess I'll try an mplayer build and see...

---

### Post by shantiq on 2011-05-29
well all things considered a star is born i guess altho is is 80 to 90 % smplayer really but with knobs on    that youtube feature really is the t*ts ; i am making it my number 1 now since VLC is still being a little bitch on my natty install , A/V sync problem on almost all video files; never has happened before

the repository version goes into freeze of the whole system with constant crunch  buzz in the tower and the twoflower 1.2 gives the A/V sync thing so grateful for the new kid on the bloc
and to second Andrew on that SMplayer still rocks but for my taste always feels like it has some "unfinished" aspects

hotkeys a nightmare when they even work
screenshot elusive almost always
but then it has the "pick up where you left off" video function and to me that is gold

VLC could really do with that one
Still hunting for the perfect player; but hey those are close and we all realize the thousands of coding hours they have required:KS

---

