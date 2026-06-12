---
title: "Edgy to Feisty with Mythtv - Should I or should I not?"
date: 2007-03-26
forum: Multimedia &amp; Video
---

### Post by newlinux on 2007-03-26
I currently have a couple mythbackend/frontend combined boxes running nicely on edgy. I've been worried about breaking things so much that I haven't been running updates lately. However, I don't want to stay too far behind and I plan on upgrading my mythfrontend only boxes to feisty. So my questions are:

[LIST=1]
[*]Will problems with myth will I probably encounter affecting mythtv when upgrading to feisty?
[*]Has there been a protocol change? Will my mythfrontends on Feisty have any problems with Edgy mythbackends if I don't upgrade the backends?
[*]What is your opinion? Should I upgrade all the boxes (when Feisty is officially released) or not?
[/LIST]

I know it may be a little early to ask these questions but I'm curious what people think.
Thanks.

---

### Post by jonny on 2007-03-26
If you're worried, you shouldn't do it.  Really.

Feisty is still pre-release software and it's highly likely something will break between now and the final release date.  You should only use it if you don't mind hosing your system or if you have the time and ability to climb out of nay pit into which you might fall.

---

### Post by newlinux on 2007-03-26
> **jonny said:**
> If you're worried, you shouldn't do it.  Really.

Feisty is still pre-release software and it's highly likely something will break between now and the final release date.  You should only use it if you don't mind hosing your system or if you have the time and ability to climb out of nay pit into which you might fall.

I realize it's pre-release now. The question is about when it is not pre-release. I understand the nature of installing it pre-release, which I definitely won't do. I'm asking about what to expect when it is released...

---

### Post by reclusivemonkey on 2007-03-26
> **newlinux said:**
> I realize it's pre-release now. The question is about when it is not pre-release. I understand the nature of installing it pre-release, which I definitely won't do. I'm asking about what to expect when it is released...

I'm running a combined mythbacked/mythfronted on Edgy. As it "just works", and I have a wireless card, I've not updated it for some time now (probably since I installed a couple of months back). However, on my desktop I have the latest Feisty with all updates. The mythfrontend works fine so far, and there has been at least one update to mythfrontend and some QT stuff since I installed Feisty (I run Gnome). I'll try to remember to post back if mythfrontend breaks ;-)

---

### Post by NT4usB on 2007-03-26
Carp... I'm nervous about updating my Dapper box to Edgy. It's working fine now and all y'all know the saying:
If it's fixed, don't break it!

I have an Edgy slave fe/be that plays nice with Dapper so updating to Edgy *might* not be painful, so I might try it... nah.
If it's fixed, don't break it!

---

### Post by majoridiot on 2007-03-28
> **newlinux said:**
> [LIST=1]
[*]Will problems with myth will I probably encounter affecting mythtv when upgrading to feisty?
[*]Has there been a protocol change? Will my mythfrontends on Feisty have any problems with Edgy mythbackends if I don't upgrade the backends?
[*]What is your opinion? Should I upgrade all the boxes (when Feisty is officially released) or not?
[/LIST]


1.&2. upgrading your frontend-only machines to feisty is safe. i have had all kinds of mixes of edgy and feisty frontends/backends working well together while testing the past couple of weeks.

3. if you have concern, wait and see if there are new problems after feisty is released.  in any event, back up you database and recordings beforehand.

---

### Post by darksong on 2007-03-28
Will you be able to upgrade from a Beta Feisty to the Final version. If you can it may be worth it as downloading the ISOs are going to be hell (with a distro as large as ubuntu, most people will want to upgrade^^) 

But saying this you may need to download as much as the ISO in data, so it may all be pointless if possible.

---

### Post by majoridiot on 2007-03-28
> **darksong said:**
> Will you be able to upgrade from a Beta Feisty to the Final version. If you can it may be worth it as downloading the ISOs are going to be hell (with a distro as large as ubuntu, most people will want to upgrade^^) 

But saying this you may need to download as much as the ISO in data, so it may all be pointless if possible.

this is a *very* good point.  my comments were predicated on a feisty install from fresh format
and then restoring your mythconverg db and recordings.

---

### Post by newlinux on 2007-03-28
yeah, I was more talking about upgrading from edgy to feisty, not reinstalling. Too many other customizations (non myth) I've made. I think I'll take a wait and see if somebody else does it approach. i just don't want my machines to get too far behind in case some new myth features that I really want come.

---

### Post by jonny on 2007-03-29
Sorry that I misunderstood your intentions a few posts back.  I'll have another go at answering your questions.

> **newlinux said:**
> 
[*]Will problems with myth will I probably encounter affecting mythtv when upgrading to feisty?
Theoretically, none.  In practice, based on previous upgrades, the most likely issues will surround the wider Ubuntu system rather than MythTV itself.  If you've enabled any 3rd party repositories, made big use of the backports facility or self-installed much software then things are much more likely to go wrong.  The most delicate parts of the system are the X server and restricted software (patent encumbered codecs, for example) and if anything breaks it'll probably be there.

> [*]Has there been a protocol change? Will my mythfrontends on Feisty have any problems with Edgy mythbackends if I don't upgrade the backends?
There shouldn't be.  MythTV is still on the same version (0.20a) as when Edgy was released, so there won't be any protocol changes unless that packagers do something bizarre.

> [*]What is your opinion? Should I upgrade all the boxes (when Feisty is officially released) or not?
That's a character thing.  Upgrading might give you a few new features, although MythTV will remain unchanged, but your system's already working and there is a risk that things will go wrong Are you a latest and greatest person?  If so, upgrade.  Or do you like things to be safe to the point of dullness?  If so, stay put. A few days ago I hosed a Dapper system whilst trying to upgrade it to Edgy; for the first time in my life I was unable to fix it and ended up wiping the slate clean and reinstalling.  If that would bother you, you need to stay with Edgy.

Me?  I'll upgrade as soon as I have time.  But I've taken a couple of important precautions: all of my systems have separate partitions for /home and for my media files, so I know that my personal data is safe no matter how badly things break.

---

