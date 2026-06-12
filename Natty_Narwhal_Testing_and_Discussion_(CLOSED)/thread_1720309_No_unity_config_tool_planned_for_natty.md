---
title: "No unity config tool planned for natty"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mc4man on 2011-04-03
Do find it interesting that atm natty will release w/ just default settings for the unity plugin and no provided config tool by default.
(the current 'experimental' options are to be considered just that.

Maybe i'm misunderstanding the intent here
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/748739](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/748739)

---

### Post by umberstark on 2011-04-03
Quite why a config tool wasn't worked on form the very beginning is beyond me. Yes you can tweak some settings via the Unity plugin for Compizconfig (although not even that is installed by default!) but not giving users some basic options (what to include on the launcher (usb drives etc).

Wow, just read Shuttleworth's comment on that bug. "Zero-config experience". So much fail in that phrase.

I want some config options thanks, like whether I want my dock full of drive icons (I have lots of them) or not etc. etc.

Just wow...

---

### Post by JRV on 2011-04-03
Yesterday I asked about this in a different thread.

My problem:

Is it possible to get rid of the "Applications" and "Files & Folders" icons at the bottom of the side bar? 
The same icons are in the dash, they are redundant.

---

### Post by macroshaft on 2011-04-03
> **JRV said:**
> Yesterday I asked about this in a different thread.

My problem:

Is it possible to get rid of the "Applications" and "Files & Folders" icons at the bottom of the side bar? 
The same icons are in the dash, they are redundant.

Agreed, I have been wondering why these were needed after the dash was made functional.

---

### Post by teachop on 2011-04-03
> **macroshaft said:**
> Agreed, I have been wondering why these were needed after the dash was made functional.
I would rather they leave them where they are and do something more helpful (to work flow) with the dash.

---

### Post by ranch hand on 2011-04-03
> **JRV said:**
> Yesterday I asked about this in a different thread.

My problem:

Is it possible to get rid of the "Applications" and "Files & Folders" icons at the bottom of the side bar? 
The same icons are in the dash, they are redundant.
And irritating.

---

### Post by VMC on 2011-04-03
> **umberstark said:**
> ...
Wow, just read Shuttleworth's comment on that bug. "Zero-config experience". So much fail in that phrase.

I want some config options thanks, like whether I want my dock full of drive icons (I have lots of them) or not etc. etc.

Just wow...+1 

Shuttleworth's amazing response, given the fact that most users like to config their system to their liking. Yes, we all know about installing CCSM, but nothing by default.

I would suggest we flood the "me too" on Doug's bug report. I did.

Shuttleworth's could have digressed a tad bit more. I too am missing the intent also.

---

### Post by mc4man on 2011-04-03
The intent of that bug was to see why there wasn't a _minimal_ config tool available to users, basically just for configuring the unity plugin and possibly general setting
I was certainly expecting one..

(I think I was fooled by the Alt+F2 > type in about:config
that will show an unity icon and open  the unity plugin settings if ccsm is installed, figured it may be replaced by a 'standalone'

ccsm isn't required to adjust the unity or any other installed plugin, it's available in gconf-editor > apps > compiz-1 > plugins, though the use of gconf-editor is more obscure than the use of ccsm

The idea that any 'simple' user, who just wishes to adjust the hide mode and or icon size of the launcher will be quite fine in finding out about and then  using ccsm is a bit absurd.

By nature people are curious - they may start opening other plugins, adjusting ect. - the opportunity to screw up the install is certainly there.

---

### Post by david stevenson on 2011-04-03
When I said I thought user choice was important on the Ayatana mailing list I was told users are welcome to choose to use something else.

---

### Post by MacUntu on 2011-04-03
> **VMC said:**
> given the fact that most users like to config their system to their liking

Can you back up this 'fact'?

I don't pretend to know what the average user wants because I really don't... I only know what I see in public places and that definitely doesn't speak for "most users like to config their system to their liking".

---

### Post by VMC on 2011-04-03
> **MacUntu said:**
> Can you back up this 'fact'?

I don't pretend to know what the average user wants because I really don't... I only know what I see in public places and that definitely doesn't speak for "most users like to config their system to their liking".

All you have to do so pay attention to this forum, and there is alot of attention given to configuration.

---

### Post by MacUntu on 2011-04-03
To answer my question: you can't.

Even if a typical forum member would represent the typical Ubuntu user (which is quite questionable) I'd find it hard to believe that you can somehow show that over 600,000 forum users configure their systems to their likings.

Moral of the story: be careful with "most users" statements if you have _nothing_ to back them up. ;)

---

### Post by VMC on 2011-04-03
:D:D> **MacUntu said:**
> To answer my question: you can't.

Even if a typical forum member would represent the typical Ubuntu user (which is quite questionable) I'd find it hard to believe that you can somehow show that over 600,000 forum users configure their systems to their likings.

Moral of the story: be careful with "most users" statements if you have _nothing_ to back them up. ;)

Let's turn it around. Can you prove otherwise. That most people don't like to configure their system...You can't either! :D:D

PS- So most people don't change their background, or re-arrange their desktop, or add icons, etc, etc. Everything is how Mark left it? Your argument is total nonsense.

---

### Post by drfox on 2011-04-03
Why don't we just say that an important number of users like to customize their systems. And perhaps those who do are more likely to be active in making GNU/Linux better.
Larry

---

### Post by VMC on 2011-04-03
> **mc4man said:**
> ...
(I think I was fooled by the Alt+F2 > type in about:config
that will show an unity icon and open  the unity plugin settings if ccsm is installed, figured it may be replaced by a 'standalone'

ccsm isn't required to adjust the unity or any other installed plugin, it's available in gconf-editor > apps > compiz-1 > plugins, though the use of gconf-editor is more obscure than the use of ccsm

The idea that any 'simple' user, who just wishes to adjust the hide mode and or icon size of the launcher will be quite fine in finding out about and then  using ccsm is a bit absurd.

By nature people are curious - they may start opening other plugins, adjusting ect. - the opportunity to screw up the install is certainly there.That "about:config" interested me also. At first I thought the plugin was installed before CCSM.

---

### Post by MacUntu on 2011-04-03
:)

---

### Post by mc4man on 2011-04-03
For the most part I think they've made the right decisions and have been fairly receptive to differing opinions (and things have been changed based on that
I think it's wrong not to provide an upfront way to adjust the launcher size, hide mode and # of workspaces, but so what, could be wrong, maybe the 'majority' will like the defaults however they are set.

Does seem that this is a bit of an invitation to install and use ccsm, which is not a bad thing per se, just curious considering that the relatively mild File Management has  not considered 'safe' for the masses to be available by default. (or for whatever reason it isn't, never managed to get an answer on that.

---

### Post by cariboo on 2011-04-03
Could we please keep things on topic.

---

### Post by el_koraco on 2011-04-03
well, if you wanna go on tweaking things, you need ccsm anyway.

---

### Post by VinDSL on 2011-04-03
Maybe desktops like this scare them...  LoL!  :D


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-3-apr-2011(2)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-apr-2011(2).png")[/INDENT]


Sorry!  I don't fit the "Zero-config experience" model...

---

### Post by webme on 2011-04-03
I've read the comments on launchpad, and it's hard to believe that a user who can't install CCSM (open USC, TYPE "ccsm", his password and press "Enter") could handle any GUI (to adjust his settings).
Mark S's choice (to leave the settings in CCSM) is natural (Unity is based on compiz) and quite good.

---

### Post by Zorgoth on 2011-04-03
The decision to leave the settings in ccsm is ok imo; users coming from windows/mac do not expect these settings to change by right-clicking, and certainly in some cases linux applications have right-click menus that are way too big.

However, there are not enough configurable options.  I hope the unity dock becomes much more powerful and customizable in the future.  At the moment I'm not using unity because cairo-dock works fine for me and fglrx, despite claims to the contrary, does not work with unity on my computer.

---

### Post by umberstark on 2011-04-04
The Windows 7 Taskbar/superbar is configured by right-clicking it. It might not have all the options you want, but there it is.

In ubuntu I shouldn't have to install a seperate software package, run it and then hunt among the stack of plugins for the one with the option to resize the dock/launcher.


Basically at the moment, in Windows a little trial and error and you'll find your way, with Ubuntu you have to go trawling forums and search engines to get the same result.

Usability fail, in a big way.

---

### Post by beew on 2011-04-04
> **VMC said:**
> :D:D

Let's turn it around. Can you prove otherwise. That most people don't like to configure their system...You can't either! :D:D

PS- So most people don't change their background, or re-arrange their desktop, or add icons, etc, etc. Everything is how Mark left it? Your argument is total nonsense.

+1000 to that. I too am sick and tired of the constant evocation of the non existent "average user" (TM)as a blanket excuse to remove/ not implement features.

Even if "the average user" ends up keeping all the defaults what is the problem of leaving the options for others? The argument that "the average user" doesn't like to configure things would be an argument for better defaults, rather than not allowing ways to change them. The sub par user doesn't have to mess with the settings if he doesn't want to, no one puts a gun to his head to force him to change anything.

By the same token I am not a very experienced user for media players so I keep all the default options but I would not say that these options should be taken away to protect me from screwing things up, if I don't feel confident I don't have to change the settings but those who know what they are doing would want them.

As you put it, the "average user" argument we have been seeing so much of late is complete and utter nonsense. It highlights a failure in design as well as communication.

---

### Post by MacUntu on 2011-04-04
> **beew said:**
> Even if "the average user" ends up keeping all the defaults what is the problem of leaving the options for others?

The options are there. You can edit them via the command line, gconf-editor, and if you installed it, the CompizConfig Settings Manager.

Pointless discussion.

---

### Post by ikt on 2011-04-04
> **MacUntu said:**
> The options are there. You can edit them via the command line, gconf-editor, and if you installed it, the CompizConfig Settings Manager.

Pointless discussion.

You feel that hiding the options away in obscure locations is ok?

At the end of the day I do sort of half agree, so long as the options are there I'm happy.

---

### Post by umberstark on 2011-04-04
> **ikt said:**
> You feel that hiding the options away in obscure locations is ok?

At the end of the day I do sort of half agree, so long as the options are there I'm happy.

They are not there on your desktop though. They are a search engine/forum trawl + software centre install away.

That is not, in any way shape or form, user friendly. And for a linux distro with serious designs on the desktop, it's quite frankly rediculous.

Seriously, what next. Removing applications from the repositories and deleting non-canonical PPA's because the default software is the way they want it with this "zero-config" approach?

---

### Post by VinDSL on 2011-04-04
> **webme said:**
> I've read the comments on launchpad [...]
I like launchpad!

There aren't any mods over there.

I just left another 'comment'.

I *think* we're breaking new ground here...  ;)

---

### Post by Zorgoth on 2011-04-04
> **MacUntu said:**
> The options are there. You can edit them via the command line, gconf-editor, and if you installed it, the CompizConfig Settings Manager.

Pointless discussion.

There aren't enough config options there anyway.  For such a massive part of your screen the Unity interface can be customized very little.

---

### Post by ikt on 2011-04-06
> **umberstark said:**
> They are not there on your desktop though. They are a search engine/forum trawl + software centre install away.

That is not, in any way shape or form, user friendly. And for a linux distro with serious designs on the desktop, it's quite frankly rediculous.

Indeed, As I have stated before, I think the zero config thing is a great aim to have, Canonical can aim to have 99% of people pleased with the defaults when they install Ubuntu with Unity, but if that 1% of people find it really annoying or difficult to do simple things with it, they may end up being the loudest critics of Ubuntu, and the distro may find some of its most dedicated leaving.

---

### Post by t1497f35 on 2011-04-06
> **ikt said:**
> Indeed, As I have stated before, I think the zero config thing is a great aim to have, Canonical can aim to have 99% of people pleased with the defaults when they install Ubuntu with Unity, but if that 1% of people find it really annoying or difficult to do simple things with it, they may end up being the loudest critics of Ubuntu, and the distro may find some of its most dedicated leaving.

99%? All the people I know change their settings in be it Mac, Window$ or Linux. The most what Mark can possibly achieve imo is make the majority not want change their settings, but not anywhere near 99%! People are just too different.
What I'd like from Mark to hear is this:
There will be a config tool for Unity with enough/many options, but we didn't have the time to create it for we barely manage to ship a plausible version of Unity with Natty, so we'll likely create such a tool later on. We're also striving to ship Unity with the best possible options and functionality enabled by default because (1) it's always a good idea and (2) because we don't yet have a mature Unity/whatnot config tool.

So far Mark's response reminds me of the past Sun's stance on Java where their ideas were excessively optimistic and based on half truths where they claimed that speed is unimportant hence Java felt slow, but when they finally created and shipped a JIT compiler with Java by default they started praising how fast Java has become. By which I mean, when companies don't yet have something others are asking for - they sometimes pretend no one needs the given feature anyway.

Bottom line, "zero-config" is only possible for a limited number of people no matter how smart the devs behind it are, the rest will continue ranting around until someone ships a plausible config tool.

---

### Post by Brian Vaughan on 2011-04-06
> **MacUntu said:**
> Can you back up this 'fact'?

I don't pretend to know what the average user wants because I really don't... I only know what I see in public places and that definitely doesn't speak for "most users like to config their system to their liking".
If someone is using Ubuntu, that means that:
[LIST=1]
[*]They installed Ubuntu on a computer that already had an operating system, probably Windows;
[*]They bought the parts for a computer and assembled it, then installed Ubuntu;
[*]They replaced a hard drive, then installed Ubuntu;
[*]They ordered a computer with Ubuntu installed, from Dell or from one of the small companies that specializes in such things, like System76 or Linux Certified;
[*]Somebody else followed one of the preceding options on their behalf.
[/LIST]
Dell no longer prominently advertises Ubuntu as an option, so someone ordering a computer with Ubuntu installed on it has made an extra effort to do it.

Only in the case of someone who's had someone else take care of setting up their computer for them is it not clear that the person will want to config their system to their liking. And then, the person who took care of setting up their computer for them may have also wanted to tweak their system for them. And, in my experience doing desktop support in corporate environments, the only people who don't config their desktop GUIs to their liking are the people who are locked out of the config applets -- and they're usually irritated about it.

Arguably, a major reason to use GUIs at all is that it's easy to config the system to a person's liking.

---

### Post by screaminj3sus on 2011-04-06
> **umberstark said:**
> The Windows 7 Taskbar/superbar is configured by right-clicking it. It might not have all the options you want, but there it is.

In ubuntu I shouldn't have to install a seperate software package, run it and then hunt among the stack of plugins for the one with the option to resize the dock/launcher.


Basically at the moment, in Windows a little trial and error and you'll find your way, with Ubuntu you have to go trawling forums and search engines to get the same result.

Usability fail, in a big way.

Agreed. Making something easy to use is great, I commend that. I really like some things about unity, but this moronic trend that options are bad is absurd. Having no easily available options, believe it or not, ACTUALLY MAKES IT HARDER TO USE. Even very novice users change at least some basic settings in windows. Saying that average users never change their settings and advanced users should have to install seperate stuff is absolutely retarded. I am linux savvy, I know how to install ccsm and change settings from there, but I shouldn't have to. Thats extra steps that waste my time.

Ubuntu is supposed to be user friendly, Mark, you are taking that motto so far that you've actually taken it to the other side of the spectrum. There needs to be some sort of unity config by default. Its absurd that there isn't.

---

