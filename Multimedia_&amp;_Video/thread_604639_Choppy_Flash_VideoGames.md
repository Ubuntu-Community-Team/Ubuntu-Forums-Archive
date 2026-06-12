---
title: "Choppy Flash Video/Games"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by Kypdurron5 on 2007-11-06
I'm running Ubuntu on a fairly low-spec PC (an old Gateway- 2ghz celeron, ~300mb RAM, onboard graphics) and I have really choppy flash.  Videos play better than games (youtube is pretty decent, livevideo is not, games are completely unplayable).  I had this problem about a year ago when I tried Linux thinking it would be better than Windows for this old computer...**but flash stuff works perfectly under Windows XP**.  Now that I've had a system corruption issue, I'm ready to try Linux again and I'd really like to make this work.  I've done several searches, but can't find anything useful...could anyone direct me to some information to go about ameliorating this issue? 

I'm otherwise very happy with the performance of this OS, but the person using this computer will primarily be using it for internet/email/and all things Java and Flash, so it's pretty important to the usefulness of the system.  Oh, and I also tried Fedora just to see if there was an overall speed difference- flash is exactly the same, but the GUI as a whole was more sluggish than Ubuntu.  

More info: I'm running the default install plus the latest (official) Adobe Flash plug-in.  

Thanks!

---

### Post by XVII on 2007-11-06
I am on a Gateway also, and I have this problem.  The choppy video and flash is just due to your low ram.

---

### Post by Kypdurron5 on 2007-11-06
> **XVII said:**
> I am on a Gateway also, and I have this problem.  The choppy video and flash is just due to your low ram.

Well I'm certainly the first the acknowledge that the low hardware specs aren't helping, but surely something that can run smoothly under a hog like Windows can do at least as well under Linux....  I'm willing to chalk it up to better driver optimization on the part of Windows, but I'm hoping there might be something I can do to improve Linux flash performance.

---

### Post by justinclark on 2007-11-25
I have 512Mb memory and flash plays VERY choppy, its un-watchable.  Any fix?

---

### Post by clesage on 2007-12-07
I am having the same problem, but I don't think it's our computers. My Flash worked fine until a couple months ago when I did an update. (I forget if it was Ubuntu, or Firefox, or Flash.)

Then suddenly, all flash-based video was choppy. I'm searching for a fix too.

I also have a lot of trouble with buffering. Whenever I watch long videos, they will randomly stop after every few minutes, and the only way I can get them to start again is by dragging the play-slider back and forth a bit.

Suggestions welcome.
Cheers.

---

### Post by GlennW on 2007-12-07
> **clesage said:**
> I am having the same problem, but I don't think it's our computers. My Flash worked fine until a couple months ago when I did an update. (I forget if it was Ubuntu, or Firefox, or Flash.)

Then suddenly, all flash-based video was choppy. I'm searching for a fix too.

I also have a lot of trouble with buffering. Whenever I watch long videos, they will randomly stop after every few minutes, and the only way I can get them to start again is by dragging the play-slider back and forth a bit.

Suggestions welcome.
Cheers.

I have similar issues. You're right when you say that it might not be our computers. I have an older P4, 1.6 Ghz, 1 Gb RAM, Geforce nVidia 6200 256 MB video card. Movies, and longer type video seem to be fine but short flash based stuff (Youtube, Metacafe, etc) are interrupted frequently.

When running XP, none of the issues mentioned here or in the above posts were apparent. 

Agreed, suggestions welcome...

---

### Post by oddworld on 2007-12-17
I am having a big problem with flash being choppy. (youtube etc...)
Any help is appreciated.
Running a dell e1405 
core 2 duo @ 2.0 ghz
2 gigs ram
intel onboard graphics

Its kinda weird that flash is so choppy, my computer is fast enough.

---

### Post by GoatTuber on 2007-12-20
Do you guys happen to have gnash installed? A friend of mine was having this same sort of problem. It seems that when you have both the gnash and flash plugins installed, firefox prefers to use the gnash one over flash, which makes it chew up resources and run really choppy. We got this fixed on his computer by completely removing both gnash and flash plugins, then reinstalling just the flash one.

---

### Post by oxleyk on 2008-01-05
> **XVII said:**
> I am on a Gateway also, and I have this problem.  The choppy video and flash is just due to your low ram.

I have to disagree.  I have Debian running on my desktop with an NVidia video adapter and 640 megabytes of RAM and Flash video is very choppy.  I also have Debian running on a notebook with an ATI video adapter and 256 megabytes of RAM and Flash video is normal.

Kent

---

### Post by GlennW on 2008-01-27
> **oxleyk said:**
> I have to disagree.  I have Debian running on my desktop with an NVidia video adapter and 640 megabytes of RAM and Flash video is very choppy.  I also have Debian running on a notebook with an ATI video adapter and 256 megabytes of RAM and Flash video is normal.

Kent

I have, after searching the forums for a couple of weeks now, come to the conclusion, as stated above, that after an unremembered upgrade, flash just ceased to work properly. The thing is that my streaming video, that finally did work well after lots of fiddling and late nights, is now choppy too, not unlike the flash (youtube, stage6). I've tried so many variations that I don't know anymore when trying another fix if I've already used that particular fix!

It appears that the flash and streaming video are independent. I'm too much of a noob to say definitively. But this is all very frustrating. I read somewhere that the flash issue is with Adobe itself. Does that mean we have to wait until they come out with a flash upgrade?

---

### Post by oxleyk on 2008-01-29
But why would it break on one and not the other?  I have the same updates on both computers.

Kent

---

### Post by ady.littlefella on 2008-01-30
I am running Ubuntu on a 1.2GHz Celeron with 512MB of RAM and flash video is very choppy.  However, I also have a Linux Mint live disk and when I boot from this on the same PC, flash is fine and not choppy at all.  As Mint is basically Ubuntu with added stuff, I am confused as to why it is so choppy in Ubuntu.

---

### Post by dannystaple on 2008-02-03
Okay - I can say with clarity that nobodies low memory is responsible for this. I see it mostly on Flash Videos (youtube), but sometimes I get choppiness or heavy CPU usage when watching videos from other sources (AVI's) as well. AVI's that play well on other boxes are showing serious lip sync issues.

My machine has 3Gb of memory, a 1.6Ghz Turion 64 CPU, A Geforce 6600 graphics card and is using an onboard sound card from the Nforce 2 350 chipset - an AC97 compatible one. This has only started in the last couple of months, so I can only surmise that some bad upgrade is responsible.

Could it be some update to ALSA or the ubuntu configuration of ALSA that has set really bad buffer settings?

---

### Post by eye208 on 2008-02-03
Do you have desktop effects enabled?

---

### Post by ady.littlefella on 2008-02-05
No, desktop effects are not enabled.  When I tried to enable them I got an error message 'Desktop Effects Could Not be Enabled'.

---

### Post by nullfactor on 2008-02-05
For what it's worth, I've been having Flash issues on my 1.6GHz Dual Core processor/ 1GB RAM machine running Gutsy.  Interestingly, my dad reported Flash issues to me shortly after the "latest / greatest" version of Flash was installed on his computer... and he uses Windows XP.

It is true that the current version of Flash is a piece of crap.  As for work arounds, sadly I haven't found any, yet... 

Good luck!

---

### Post by ady.littlefella on 2008-02-09
But, how come Linux Mint appears to have the latest flash and it works fine.  They must be doing something that we're not !!!

---

### Post by oddworld on 2008-02-09
I thought Linux Mint had a little ubuntu under it?
And shouldnt "flash" be the same for all linux OS?

---

### Post by nilarimogard on 2008-02-09
I had the same problem with flash, but then i went back to version 9r48 and everything is much better. You should give it a try. Here's where you can download it: [http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip)

From that archive, remember to install 9r48 and not the latest driver

---

### Post by yammosk on 2008-03-08
I don't get it, I've got a Radeon 9600, 1 GB of RAM and youtube is very choppy, especiall in full screen. Playing AVIs in VLC is super-smooth though. I can't find a fix for this. :(

---

### Post by oddworld on 2008-03-08
I have just come to the conclusion that until adobe releases their open source code that we will all be without 100% working flash.
My flash works well now, I can watch youtube without too much lag.
But until those drivers are perfect, we may not see the full benefits.
Am I right?

---

### Post by theaceoffire on 2008-03-10
I have a short term fix for this issue, although it is not perfect.

See, VLC will play the flash easily, with little CPU usage...

So I made a script that gives you the direct video link so that you can click and play/save videos automatically when you go to the page.
[http://ubuntuforums.org/showthread.php?t=720350](http://ubuntuforums.org/showthread.php?t=720350)

---

### Post by Spacenoodle on 2008-03-11
I have this same problem, i'm running an old laptop with 512mb of ram, for websites like metacafe the video doesn't play at all, and in youtube it's too choppy to watch. Is there a fix for this?

---

### Post by VMOS on 2008-03-11
looks like i'm having similar problems, video runs at normal speed (usually) but will always stutter at least once (usually more) like it's having buffering problems
[http://ubuntuforums.org/showthread.php?t=684735](http://ubuntuforums.org/showthread.php?t=684735)

runs fine with theaceoffire's script but not when embedded

---

### Post by ihatethetv on 2008-06-27
I'd say it's probable video card drivers.  Copying from toher thread::

I was running into this problem too with my 8600GT...I pulled it and tried my ATI onboard video just for kicks...turns out that fixed it...or at least made it a lot better.

This suggests to me that it's a video driver problem. I'm running the most current nvidia driver as of today 6/27/2008.

I went over and bellyached at nvidia in their forums here: I encourage you to do so as well if you're having this problem.

[http://forums.nvidia.com/index.php?s...5&#entry401485](http://forums.nvidia.com/index.php?s...5&#entry401485)

Good luck,
Glen

---

### Post by zieglerj on 2008-07-11
it's deffinetly not the RAM. I'm having the exact same problem that started at about the same time and I'm running 4GB of RAM.

---

