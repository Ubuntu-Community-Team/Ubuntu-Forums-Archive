---
title: "Sony Vegas Style Video Editor?"
date: 2007-02-21
forum: Multimedia &amp; Video
---

### Post by tsav87 on 2007-02-21
Is there any Linux alternative to Sony Vegas that I can use to edit videos and add in affects and stuff?

---

### Post by MetalMusicAddict on 2007-02-21
> **tsav87 said:**
> Is there any Linux alternative to Sony Vegas that I can use to edit videos and add in affects and stuff?

PiTiVi, Cinelerra and LiVES are your best bet. I think you will be disappointed though. NVE apps in linux need alot of work.

---

### Post by benplanet on 2007-07-03
Was looking for one myself... Lives is nowhere near vegas or premier ... i guess i'll have to give wine a try :)

---

### Post by yodermk on 2007-07-03
I think Cinelerra is a pretty good program.  Granted I'm not a video expert.

Just curious, how specifically in Vegas or Premiere better than Cinelerra?

---

### Post by benplanet on 2007-07-04
never heard of it! does it work on feisty 64bit ?

---

### Post by Blessed_Coffee on 2007-12-09
Cinelerra looks pretty good.  I'm downloading it now.  Sony Vegas is the only thing I miss from windows.  I hope Linux has something close.  It would be lame to duel boot just to use a video editor...

---

### Post by ceejay on 2007-12-13
Like others I'm looking for an editor to use on Ubuntu - doesn't need to be fancy, mainly for editing adverts and other stuff out of MPEGs recorded off-air.  Using Gutsy on an Intel Dual Core 64.

I tried openmovieeditor - it downloaded ok but didn't run well and didn't handle by-frame trimming of an MPEG.

I'd like to try cinelerra but don't seem to be able to download it.  I think I followed the directions at [http://cv.cinelerra.org/getting_cinelerra.php](http://cv.cinelerra.org/getting_cinelerra.php) including specifying the repository "deb [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./" in package manager but the package doesn't then show up. Any suggestions?

TIA.

---

### Post by HuwSy on 2007-12-13
Cinelerra is also avail from [http://repoubuntusoftware.info/](http://repoubuntusoftware.info/) which should have all the dependancies in there repository too. But be warned they also have some miss version numbered packages. So remember to remove/disable there repository after installing cinelera otherwise next time you upgrade youl go back a few versions and even over a year on some packages.

As for a good alternative to vegas or even premiere, its not really. Its nice for simple things but anything more involved i think only vegas will do. Hopefully the next version of mono for wine will be enough .net 3 supporting to run vegas.

---

### Post by galvheim on 2007-12-13
As lame as it might be, I have a dual-boot system for the only purpose of having good video-editing software. I installed vegas just before I went Ubuntu-style, but before that I used StudioDV for speed-editing, premiere for post-effects like steadycam, glow, and some others. 

The other thing we seem to lack on linux is a very fast, simple yet advanced compression tool like my favorite Virtualdub for use with codecs like DivX Pro and Xvid. 

In video Windows is far in front of Linux. Hopefully this will change some day. In my search for good alternatives I found nothing but very simplistic and basic software for ubuntu. So until we have two suns shining on the same sky I will stick to the lame dual-boot.

---

### Post by xenxor on 2007-12-13
we have Avidemux as very competent replacement for virtualdub.  it supports even x264.

---

### Post by ceejay on 2007-12-15
> **ceejay said:**
> 
I'd like to try cinelerra but don't seem to be able to download it.  I think I followed the directions at [http://cv.cinelerra.org/getting_cinelerra.php](http://cv.cinelerra.org/getting_cinelerra.php) including specifying the repository "deb [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./" in package manager but the package doesn't then show up. Any suggestions?



Answering my own question - it appears I made a mistake in believing the comment on the cinelerra download page about using the amd64 build also for Intel Core Duo. I went for the i386 version instead and have successfully downloaded and run the package.

Now I'm stuck at the next hurdle: what I really want to do is just to (1) load in an MPEG file (typically recorded off-air, having been transcoded from TS stream by mencoder) then (2) trim the start, end, and if necessary adverts before (3) saving back to MPEG for viewing later.

It looks like I can do steps (1) and (2) with cinelerra, but I'm failing at step (3) as it appears not to have the capability to save/render to MPEG. Am I missing something?

TIA

---

### Post by doorknob60 on 2007-12-22
I too wish there were better video editors for linux. I use VirtualBox for the sole purpose of Windows Movie Maker and Sony Vegas, it's kinda sad but even Windows Movie Maker is better than anything available for Linux. Although KDEnlive looks promising, it has some bad bugs right now.

---

### Post by HuwSy on 2007-12-22
Iv just started trying open movie editor which has potential but keeps crashing on me with some of the video clips i have. Other than that the best thing currently still being developed is pitivi imo. And somewhere iv seen an image of it with multiple video tracks on a timeline a'la premiere. But never managed to find a version myself that supports this. Still think il sit and await .net3 on wine, as i really dont want a virtual machine as a solution, it defeats the object of moving away from windows completely.

---

### Post by MunchyBugs on 2008-01-03
I have Ubuntu on two machines but just for fun.  I tried all the Linux NLEs but they are all nearly 100% useless compared to what the corps put out.  There is nothing near Vegas or Priemre.  Add to that all the other utility of CS3 (After Effects, Photoshop, etc) and all the integration those offer and there is no way I could ditch windows in the foreseeable future.  Professionals like me have all we can do to maintain an expertise in what is out there now, let alone helping to develop something for a new OS from the ground up...not going to happen.  The only way you'll be able to do any useful multimedia stuff on Ubuntu ever is if Adobe offers their software for it, or if someone like Dreamworks or WB or Sun funds it.  Probably not going to happen.

Sorry, thats the reality of it under capitalism.

---

### Post by HuwSy on 2008-01-03
The other option would be for apple or sgi to release there suites of unix based video software that they both have since they made there moves to a unix. Its nothing hard for either company to port it realistically, its wether they see it as profitable enough to be worth killing off there own tied in hardware solutions. So something that will really never happen. Think the best solution imo is to get a mac at this rate.

---

### Post by lavinog on 2008-06-24
I have been using Sony Vegas since it was Sonic Foundry video factory 1.0
It is the thing I miss most from my windows box (recently retired)
I haven't needed much for video editing for the past couple of years, but now I am looking for something that can do what Vegas did with pictures.
Does anyone know what software can create panning paths with images (kind of like a manual ken williams effect)
I suspect blender can do what I am looking for, but I find it intimidating since I have a 2 week time frame.
Any info would be helpful.

---

### Post by HuwSy on 2008-06-25
open movie editor is about the best iv found pure linux wise, or using wine and finding via google winetricks to install dot.net 1 then 2 (not mono as its not there yet) then vegas 6 or 5, vegas 7 doesnt work cant remmber which did tho.

---

