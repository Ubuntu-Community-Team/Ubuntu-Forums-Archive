---
title: "Mythbuntu + DRM = WTF FCC"
date: 2010-12-18
forum: Mythbuntu
---

### Post by scooter28 on 2010-12-18
After years of thinking about it, I've finally decided to build a HD media center.  However, after researching my hardware options, I am now extremely frustrated!

Basically, I want a DVR that can grow as my media collection does, that can record HD from my cable company, and can play Blu-Ray movies.  Given all the available technology that doesn't seem to to be too much to ask.

So, this [http://www.cetoncorp.com/buy.php](http://www.cetoncorp.com/buy.php) seemed the best solution for a capture card since it lets me get all the HD content I currently pay for.  That is until I found out it only works with Windows 7 Media Center.  I don't think I really have to explain this here, but I don't use Windows, ever.  Next problem: even if I did use Windows, and buy this card, my cable company (Time Warner Cable) apparently flags all content with Copy Once DRM, so I would be stuck with all my HD content on one HDD for ever.  Thus no RAID, no streaming, no backup, no getting a bigger HDD as my collection grows, etc.

I also found out that Verizon and some other providers leave the Copy Once flag off on their content and it is actually supposed to be up the network to decide whether the flag is set or not.

So finally, on to the point of this post: How, in the supposedly freest country on Earth, is it up to the discretion of one company how and where I use the content that I pay for?  Now they also have control of the computer hardware and software decisions I make?  Hasn't Microsoft already gotten into trouble as a software monopoly?  Now CableLabs is exclusively certifying Windows based PCs?  Is the FCC even aware of the decisions CableLabs and content providers make and how that effects consumers?

This may be the wrong forum for such discussions, but it seems to me to be a severe infringment on our rights and freedoms as Americans and we as Linux/Unix users are exclusively effected by this.  Mostly I looking for a sympathetic ear, but an open source political revolution would be cool too.

I don't know what the solution is, but it seems to me that TWC shouldn't legally be able to make DRM decisions that are meant to be made by the networks and CableLabs really can't create a HD MCPC monopoly with Microsoft.  It ought to be illegal, and if it isn't I still think we'd have a pretty good civil case.  Any Thoughts?

---

### Post by Psyael on 2010-12-18
You have no rights to cable television. You likewise have no ownership rights to the programs being broadcast. You take it or leave it. And it's got little to do with America, just take a look at how many countries News Corp runs a Sky Satellite service in. You voluntarily pay them to provide you a service, that's about it.

However, it is illegal for them to scramble the local affiliate stations (they may do it anyway, since few people bother to check, but they're not supposed to.) This means any tuner that supports unencrypted QAM such as the HD HomeRun can use them just fine.

All that said, I love Linux and would promise anyone not into heavy gaming to use it for their desktop, but although I've tried I really don't see the benefits to Myth at this point in time as it requires jumping through too many flaming hoops and the upstream devs are getting somewhat bossy themselves (such as how in .24 they merged menu themes and OSD themes and told the community to just deal with it.) As a media collector/indexer/player it's still number one or two depending on if you prefer XBMC, but for live TV and scheduling it almost painful comparing MCE's simplified choices to Myth's myriad setup screens.

If it means that much to you, though I wouldn't use Win7 for anything else, 7MC "just works." And it can be modded to heck and gone with custom themes, web scheduling, commercial skip, Netflix integration, and so on. It still has limitations and little pains like any piece of software, but I'm just never one to deny myself content over my political positions.

---

### Post by LowSky on 2010-12-18
There is a way around DRM.. it called the Haupauge HD PVR - Check it out
It isn't the prettiest solution but it does what you want.

---

### Post by jarnett on 2010-12-30
Define "not the prettiest solution".

---

### Post by AKADAP on 2010-12-31
> **jarnett said:**
> Define "not the prettiest solution".

It takes advantage of the "analog hole" so the quality is not quite as good as a direct digital copy. It is expensive, and requires rental of a cable box.

If your cable company attempts to close the "Analog Hole", look into the HDFury.

---

### Post by williammanda on 2010-12-31
Either I'm lucky or drm doesn't effect cable tv here. Comcast to me is the worst and that is what I have. I'm able to record tv programs without any restriction. If you are restricted from recording basic tv programming then you need to look else where ie OTA. I'm not familiar with DRM on TV broadcasts in the US. Otherwise Mythtv is an excellent dvr except for the lack of ripping dvd in version .24 but programs like Makemkv help out in that area. I basically agree with your rant but that is world we live in.

---

### Post by BicyclerBoy on 2010-12-31
There are also soft cams allowing use/sharing "cards" so one card reader can allow many front-end machines.
This can allow much more flexible/useable encrypted content than STB (dvb-s or cable)

sasc-ng
newcs
Cccam

These are not illegal in some countries. You can use legal legit "cards" supplied by the content provider. 
Fortunately, in my part of world, the FTA content is still okay.

---

### Post by jmore9 on 2011-05-04
Recording cable tv today in my area means you must have a cable box period.  comcast in this area has swiched to all digitial and encrypted.  There are very few QAM stations left. There are no basic packages anymore.  Digital Starter is the 1st package i believe.  If i am mistaken please correct me.

When you get your cable or OTH for that matter hooked up you still have the possibility of using a vcr but it would go between the cable box and the tv.

If you are going to use a tv tuner card then i would suggest that you get one that has on board processing.  Not the ones that use the cpu to do the work.  I have a tv wonder 650 pro pci and it picks up OTH ok.  It records it OK.  The only problem is this card is about 6 , 7 years old and there is no support in linux and getting it to work in Win 7 was a huge hassle.

There are several hauppauge ( I think i got the name right ) tuner cards that are very goos and have support in linux.

there are also cpu intensivve cards from pctv ( hauppauge owned also ) called pinnacle 800i which work with linux.

If in doubt whether a tv tuner card will wrok in linux you should go to 

linuxtv.org  this is the source on tv in linux.

And not all tv tunner cards have support the broadcast flag you would have to check each one you like.

Hope this helps in some way

---

