---
title: "Clean up nautilus UI (nautilus-elementary)"
date: 2010-05-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by screaminj3sus on 2010-05-23
Nautilus's UI takes up lots of unnecessary space and can be cleaned up a lot. Ubuntu has been making lots of nice UI changes lately and I think this would be a good one. Nautilus elementary is already doing this very nicely. I think they should use nautilus-elementary by default or make some similar changes.

[img]http://img571.imageshack.us/img571/2249/screenshotk.png[/img]

---

### Post by ranch hand on 2010-05-23
I have heard of this before and did a little research.  It really does look like they have done a real nice job on it.

Then I paid attention to what I was doing when in nautilus and realized that this was not for me at all as I use most of the current features.

Therefore I think going with the current default would be a better idea so that folks new to Gnome can see and use the whole thing.

That said I think that nautilus-elementary should be in the repo so that it is easier to get for those same new folks.

A lot of people do not use the file manager anywhere near as much as I do.  This would be a real nice tool for them.

It boils down to  what ought to be the default.  I think full blown apps are the thing to use so that folks know what they use or do not use.  That way they can get rid of things rather than not know they are out there.

---

### Post by Merk42 on 2010-05-23
in b4 mac..

Seriously though, isn't nautilus getting a makeover for GNOME 3? If so wouldn't it just be better to follow upstream?

---

### Post by gnomeuser on 2010-05-23
> **Merk42 said:**
> in b4 mac..

Seriously though, isn't nautilus getting a makeover for GNOME 3? If so wouldn't it just be better to follow upstream?

The only change to nautilus I am aware of in the GNOME3 realm is the split pane work (and that malfeature luckily seems to have gathered the ire of the usability people).

So I doubt that is a good approach.

Another idea might be to skip Nautilus all together, the [Dash](http://danrabbit.deviantart.com/art/Dash-File-Browser-158744102) file manager ([Dash on Launchpad](https://launchpad.net/dashfilebrowser)) e.g. looks promising from a UI stance and as a bonus it's written in a modern productive language.

---

### Post by screaminj3sus on 2010-05-23
Right now nautilus is too integrated into gnome to easily ditch though (doesn't it manahge desktop icons and such?)

---

### Post by gnomeuser on 2010-05-23
> **screaminj3sus said:**
> Right now nautilus is too integrated into gnome to easily ditch though (doesn't it manage desktop icons and such?)

Nautilus is a core part of GNOME but it isn't impossible to replace it. Managing the desktop e.g. is a feature that can be disabled (via a handy gconf key: apps->nautilus->preferences->show_desktop)

It is likely a bit more work than replacing most other applications though, but in no way should that stop interested people from trying.

---

### Post by BwackNinja on 2010-05-23
I wouldn't say all of the changes in nautilus-elementary should be included, but the improved categorized sidebar is definitely better than the current. I'm surprised that the new pcmanfm isn't mentioned more when there is talk about file managers. It is even in the lubuntu ppa for an easy install and is mostly stable.

---

### Post by ranch hand on 2010-05-23
> **BwackNinja said:**
> I wouldn't say all of the changes in nautilus-elementary should be included, but the improved categorized sidebar is definitely better than the current. I'm surprised that the new pcmanfm isn't mentioned more when there is talk about file managers. It is even in the lubuntu ppa for an easy install and is mostly stable.
pcmanfm2 really is nice isn't it?  I like nautilus but that is number 2 on my list anyday.  I have used it on Gnome Ubuntu even.

It is the reason I have Lubuntu on here right now.

---

### Post by screaminj3sus on 2010-05-24
my issues with pcmanfm and thunar are you cant browse windows shares easily like nautilus. They both are way faster, especially opening folders which is where nautilus seems super slow with big folders.

---

### Post by ranch hand on 2010-05-24
> **screaminj3sus said:**
> my issues with pcmanfm and thunar are you cant browse windows shares easily like nautilus. They both are way faster, especially opening folders which is where nautilus seems super slow with big folders.
Well, I can see that could be a problem for those who have the misfortune to be afflicted with MS.

I don't like thunar all that well but it does work.

I believe that the problem you bring up is currently being addressed in the development of pcmanfm2.  If you have not tried the new one it might be better than you remember.  I wouldn't know, I do not do windows.

---

### Post by gnomeuser on 2010-05-24
> **screaminj3sus said:**
> my issues with pcmanfm and thunar are you cant browse windows shares easily like nautilus. They both are way faster, especially opening folders which is where nautilus seems super slow with big folders.

No worries they are about at equal footing currently with regards to this. Which is worse, not having support or having support that seems to break every other release?

[https://bugs.launchpad.net/bugs/481197](https://bugs.launchpad.net/bugs/481197)

---

### Post by Longinus00 on 2010-05-24
> **gnomeuser said:**
> 
Another idea might be to skip Nautilus all together, the [Dash](http://danrabbit.deviantart.com/art/Dash-File-Browser-158744102) file manager ([Dash on Launchpad](https://launchpad.net/dashfilebrowser)) e.g. looks promising from a UI stance and as a bonus it's written in a modern productive language.

A C# file manager? Not even microsoft is that crazy :confused:. Get back to us when fedora switches over.

---

### Post by zekopeko on 2010-05-24
> **gnomeuser said:**
> The only change to nautilus I am aware of in the GNOME3 realm is the split pane work (and that malfeature luckily seems to have gathered the ire of the usability people).

So I doubt that is a good approach.

Another idea might be to skip Nautilus all together, the [Dash](http://danrabbit.deviantart.com/art/Dash-File-Browser-158744102) file manager ([Dash on Launchpad](https://launchpad.net/dashfilebrowser)) e.g. looks promising from a UI stance and as a bonus it's written in a modern productive language.

The saddest part is that there are plenty of patches in the bugzilla for Nautilus, but the devs are just letting them rot there. There was even a GSoC proposal about Clutter-ifying Nautilus but guess what, it was killed by the lead dev.

---

### Post by zekopeko on 2010-05-24
> **Longinus00 said:**
> A C# file manager? Not even microsoft is that crazy :confused:. Get back to us when fedora switches over.

Since when do Ubuntu users care for what Fedora does? And that "C# is slow meme" needs to die. Dash is fast and it was a two week hack job by somebody who never programmed in their life.

---

### Post by Longinus00 on 2010-05-24
> **zekopeko said:**
> Since when do Ubuntu users care for what Fedora does? And that "C# is slow meme" needs to die. Dash is fast and it was a two week hack job by somebody who never programmed in their life.

I never said it was slow, I just said not even microsoft was that crazy. ;)

---

### Post by zekopeko on 2010-05-24
> **Longinus00 said:**
> I never said it was slow, I just said not even microsoft was that crazy. ;)

You'll have to define crazy in this context.

BTW MS was crazy enough to use C# and XAML in their Phone 7 OS. Crazy people. Using C# on ARM devices. I mean really...

---

### Post by Kazade on 2010-05-24
> **zekopeko said:**
> Since when do Ubuntu users care for what Fedora does? And that "C# is slow meme" needs to die. Dash is fast and it was a two week hack job by somebody who never programmed in their life.

I don't think anyone is suggesting that C# is slow. I think the question is more about whether any potential performance hit and increased memory usage is worth it compared to writing in something like Vala that compiles down to asm?* And would it get to a point where the memory/CPU usage caused by C# will be the bottle-neck in displaying folders with many-many files with previews enabled?

Personally, I'd like my file manager to be non-dependent on the mono runtime, simply because it's something that's running all the time and I like my base system to be pretty slim - but that's just me**

Anyway let's not turn this into another mono/language flamewar. I think both Dash and Nautilus-elementary look really nice, but I'd suggest if we are going away from vanilla Nautilus that we stick to the more mature, more widely tested Nautilus-elementary with the prospect of merging the patches back to vanilla Nautilus.

*(I'm aware that C# can potentially be as fast as a compiled language but you tend to have to work a bit more for that performance)

** Cue the "we have so much memory these days" comments :p

---

### Post by zekopeko on 2010-05-24
> **Kazade said:**
> I don't think anyone is suggesting that C# is slow. I think the question is more about whether any potential performance hit and increased memory usage is worth it compared to writing in something like Vala that compiles down to asm?* And would it get to a point where the memory/CPU usage caused by C# will be the bottle-neck in displaying folders with many-many files with previews enabled?

Personally, I'd like my file manager to be non-dependent on the mono runtime, simply because it's something that's running all the time and I like my base system to be pretty slim - but that's just me**

Anyway let's not turn this into another mono/language flamewar. I think both Dash and Nautilus-elementary look really nice, but I'd suggest if we are going away from vanilla Nautilus that we stick to the more mature, more widely tested Nautilus-elementary with the prospect of merging the patches back to vanilla Nautilus.

*(I'm aware that C# can potentially be as fast as a compiled language but you tend to have to work a bit more for that performance)

** Cue the "we have so much memory these days" comments :p

I do believe Nautilus would benefit from a complete rewrite. Or at least merging some features that have patches in the bugzilla.
Look for example the new sidebar nautilus-elementary has (Personal, Storage device etc with the little expanders). That feature has a patch in the bugzilla but was never applied. There are plenty of patches in the nautilus bugzilla but the devs never apply them.

The lead dev of nautilus basically asked a potential GSoC student what does Clutter-fying Nautilus bring to users, like there was no benefit. But he has no problem with Gnome-shell. It's like nautilus devs don't understand that their file browser is used by actual users besides them.

---

### Post by Merk42 on 2010-05-24
> **zekopeko said:**
> The lead dev of nautilus basically asked a potential GSoC student what does Clutter-fying Nautilus bring to users, like there was no benefit. But he has no problem with Gnome-shell. It's like nautilus devs don't understand that their file browser is used by actual users besides them.

Of course he wouldn't have a problem with GNOME Shell, it doesn't touch Nautilus

---

### Post by zekopeko on 2010-05-24
> **Merk42 said:**
> Of course he wouldn't have a problem with GNOME Shell, it doesn't touch Nautilus

[http://www.mail-archive.com/nautilus-list@gnome.org/msg05668.html](http://www.mail-archive.com/nautilus-list@gnome.org/msg05668.html)

---

### Post by gnomeuser on 2010-05-24
> **zekopeko said:**
> [http://www.mail-archive.com/nautilus-list@gnome.org/msg05668.html](http://www.mail-archive.com/nautilus-list@gnome.org/msg05668.html)

I don't really see the problem. Just saying "let's use Clutter" isn't really addressing an issue or proposing a specific improvement.

That's the same as saying let's use Vala.. for what? Why? Do you hate life?

I think the approach Dash and Nautilus Elementary takes is more productive. It is about concrete improvements rather than the technology used to implement them.

I just switched my machine to Nautilus-elementary and I have to say it is visually and functionally an improvement. I still wish they would remove the pointless tab feature which only serves to add complexity and ui uglyiness. I haven't tried compiling Dash yet, the project looks interesting and I certainly would be interested in contributing to it. Perhaps later today.

---

### Post by zekopeko on 2010-05-24
> **gnomeuser said:**
> I don't really see the problem. Just saying "let's use Clutter" isn't really addressing an issue or proposing a specific improvement.

That's the same as saying let's use Vala.. for what? Why? Do you hate life?

I think the approach Dash and Nautilus Elementary takes is more productive. It is about concrete improvements rather than the technology used to implement them.

I just switched my machine to Nautilus-elementary and I have to say it is visually and functionally an improvement. I still wish they would remove the pointless tab feature which only serves to add complexity and ui uglyiness. I haven't tried compiling Dash yet, the project looks interesting and I certainly would be interested in contributing to it. Perhaps later today.

Here is the next mail. [http://www.mail-archive.com/nautilus-list@gnome.org/msg05677.html](http://www.mail-archive.com/nautilus-list@gnome.org/msg05677.html)

I would say that the point is to have a flexible canvas where people could do all sorts of crazy things through plugins.

---

### Post by screaminj3sus on 2010-05-24
> **ranch hand said:**
> Well, I can see that could be a problem for those who have the misfortune to be afflicted with MS.

I don't like thunar all that well but it does work.

I believe that the problem you bring up is currently being addressed in the development of pcmanfm2.  If you have not tried the new one it might be better than you remember.  I wouldn't know, I do not do windows.

I've tried the one in the ubuntu 10.04 repos (0.5.2 I think) It doesnt seem to have the ability to browse any network shares that I can see.

---

### Post by 23meg on 2010-05-24
> **zekopeko said:**
> The lead dev of nautilus basically asked a potential GSoC student what does Clutter-fying Nautilus bring to users, like there was no benefit. But he has no problem with Gnome-shell. 

> **zekopeko said:**
> I would say that the point is to have a flexible canvas where people could do all sorts of crazy things through plugins.

GNOME Shell is notably different in that it's not about "let's use a cool new technology to let people do crazy things". It has had well-defined goals and design specs almost from the start.

I can totally understand how an already busy maintainer would not want to spend time mentoring a project based on such a poorly defined proposal. Larsson is generally very good at [saying the right "no"s]("http://ometer.com/features.html").

---

### Post by gnomeuser on 2010-05-24
Some further Nautilus Elementary notes:

"System" is a rather confusing link to / which should never be needed by a user. 

I quite like how the Computer metaphor has been replaced with the sidepane. It is very elegant but device actions do not appear to be allowed currently. Meaning that to copy a DVD to an ISO image I can't right click the DVD and select Copy, I can't go to the Computer easily either since that was removed.

In the same vein I don't really see the point of having a direct link to the home dir. All the data one might want to interact with should be located in subfolders and there should really not be a need in any general case for going to ~.

In other words.

The System device should be removed, likewise the home dir shortcut and device actions should be added to the sidepane.

---

### Post by zekopeko on 2010-05-24
> **23meg said:**
> GNOME Shell is notably different in that it's not about "let's use a cool new technology to let people do crazy things". It has had well-defined goals and design specs almost from the start.

I can totally understand how an already busy maintainer would not want to spend time mentoring a project based on such a poorly defined proposal. Larsson is generally very good at [saying the right "no"s]("http://ometer.com/features.html").

So you're saying people won't "go crazy" with Gnome-shell. Right.

I still think that having a clutter-fied nautilus with a good extension system could have made it THE file manager/browser on any OS. It would enable all kinds of things.
The fact that nautilus elementary is so popular speaks to the fact that nautilus fails in a number of areas.

---

### Post by 23meg on 2010-05-24
> **zekopeko said:**
> So you're saying people won't "go crazy" with Gnome-shell. Right.

No, I'm saying that the point of G-S isn't technologies that let people go crazy, that Clutter is just one piece of technology that happens to make the desired G-S experience possible, and that G-S and this proposed Clutter-based Nautilus only have using Clutter in common.

> **zekopeko said:**
> I still think that having a clutter-fied nautilus with a good extension system could have made it THE file manager/browser on any OS. 

Maybe, maybe not. My point is that this *particular* proposal has fallen short of making a good case of its usefulness, and that thus it's more than understandable that the already understaffed Nautilus maintainers may not want to mentor it. 

[QUOTE=zekopeko]It would enable all kinds of things.[/QUOTE]

In the context of developing highly usable and learnable software for mainstream use, that's usually the *problem* with new technologies, not the magic: now that you have a new piece of tech that enables "all kinds of things", what are the particular things that you want to do with it? Where do you want to go? What are the pieces of that technology that you can utilize towards your goals? Projects / proposals that fail to answer such questions satisfactorily are destined to be technology demonstrators at best.

---

### Post by Seventh Reign on 2010-05-24
I dont particularly dislike the default Nautilus, however I do install Nautilus-Elementary as soon as I install a new system.  It just feels ... right.

---

### Post by vkontakte on 2010-05-25
> **gnomeuser said:**
> Some further Nautilus Elementary notes:

"System" is a rather confusing link to / which should never be needed by a user. 

I quite like how the Computer metaphor has been replaced with the sidepane. It is very elegant but device actions do not appear to be allowed currently. Meaning that to copy a DVD to an ISO image I can't right click the DVD and select Copy, I can't go to the Computer easily either since that was removed.

In the same vein I don't really see the point of having a direct link to the home dir. All the data one might want to interact with should be located in subfolders and there should really not be a need in any general case for going to ~.

In other words.

The System device should be removed, likewise the home dir shortcut and device actions should be added to the sidepane.

I like the fact you are not nautilus dev :)

---

### Post by screaminj3sus on 2010-05-25
> **gnomeuser said:**
> Some further Nautilus Elementary notes:

"System" is a rather confusing link to / which should never be needed by a user. 

I quite like how the Computer metaphor has been replaced with the sidepane. It is very elegant but device actions do not appear to be allowed currently. Meaning that to copy a DVD to an ISO image I can't right click the DVD and select Copy, I can't go to the Computer easily either since that was removed.

In the same vein I don't really see the point of having a direct link to the home dir. All the data one might want to interact with should be located in subfolders and there should really not be a need in any general case for going to ~.

In other words.

The System device should be removed, likewise the home dir shortcut and device actions should be added to the sidepane.
Don't see how "system" is any worse than what default nautilus calls it ("filesystem")

---

### Post by ammonkey on 2010-05-25
> **gnomeuser said:**
> Some further Nautilus Elementary notes:

"System" is a rather confusing link to / which should never be needed by a user. 

I quite like how the Computer metaphor has been replaced with the sidepane. It is very elegant but device actions do not appear to be allowed currently. Meaning that to copy a DVD to an ISO image I can't right click the DVD and select Copy, I can't go to the Computer easily either since that was removed.

In the same vein I don't really see the point of having a direct link to the home dir. All the data one might want to interact with should be located in subfolders and there should really not be a need in any general case for going to ~.

In other words.

The System device should be removed, likewise the home dir shortcut and device actions should be added to the sidepane.

Interesting i like your device actions idea. Maybe we can define some action device list we wish to be implemented in nautilus-elementary.

edit:
"I can't go to the Computer easily either since that was removed."
why would u go in computer:// ? since all the items listed under the category "Devices" is the content of computer://

---

### Post by zekopeko on 2010-05-25
> **ammonkey said:**
> Interesting i like your device actions idea. Maybe we can define some action device list we wish to be implemented in nautilus-elementary.

edit:
"I can't go to the Computer easily either since that was removed."
why would u go in computer:// ? since all the items listed under the category "Devices" is the content of computer://

Hey can you try and use Archive Mounter to mount a rar or a zip file? They show under the Network and not under Personal where i would expect them.

---

### Post by ammonkey on 2010-05-25
> **zekopeko said:**
> Hey can you try and use Archive Mounter to mount a rar or a zip file? They show under the Network and not under Personal where i would expect them.

yes i know the bug is already registered ;)

[https://bugs.launchpad.net/nautilus-elementary/+bug/583191](https://bugs.launchpad.net/nautilus-elementary/+bug/583191)
all that don't have a volume goes in network for the moment. Still looking for a good function to use in gio. Gmount-iso works ok.

---

### Post by screaminj3sus on 2010-05-25
Anyone else having issues with launchpad? I am attemtpign to file a packaging request for nautilus-elementary so I can get the ubuntu brainstorm idea opened up if it gets packaged, when whenver I hit sumbit launchpad is giving me timeout errors. :/

---

### Post by ammonkey on 2010-05-25
nautilus-elementary is already packaged:
ppa:am-monkeyd/nautilus-elementary-ppa

---

### Post by screaminj3sus on 2010-05-25
Yeah but on brainstorm they said it had to be in the ubuntu repos, or else they dont even consider testing it or including it by default.

---

### Post by zombiepig on 2010-05-25
Don't know if anyone's seen this yet, but it does look like there'll be some visual improvements in line for nautilus:

[http://live.gnome.org/Nautilus/UIRoadmap](http://live.gnome.org/Nautilus/UIRoadmap)

A change has already been merged to make icons dim after cutting, and on that list is a bunch of the stuff that's been talked about here (side panel, toolbar layout, search box)

---

### Post by KdotJ on 2010-08-12
To revive an old thread...

does anyone know if nautilus-elementary is going to make the repos for maverick??

---

### Post by screaminj3sus on 2010-08-15
I put in a  request for packaging around the time I made this thread but haven't checked it since.

---

### Post by ammonkey on 2010-08-15
nautilus-elementary can't be in official repository because it replace an existing package (nautilus). To be packaged in an official repository it take to rewrite too many components to get separates binaries/libs. And even if this rewrite occur there's no simple way in gnome to configure and choose which filemanager u want to use. i am talking about the desktop, the gnome-panel etc ...

Like many years with the web browsers we're stuck with the default choice with no simple way to use another application. That's why the easiest way for nautilus-elementary was to replace nautilus package and that's why you won't see it in any official repositories.

---

### Post by libssd on 2010-08-15
Nautilus-elementary is one of those hard to discover (unless someone tells you about it) things about Ubuntu that makes you scratch your head about why it's not included by default. It could make the UI experience so much easier for a new user, for whom installation may be beyond the comfort zone. I set up a Mint system for a friend (whose experience was entirely with Windows), and included N-E; she immediately understood it without explanation, and was extremely happy when I mentioned the F3 split window function.

People in *nix-land always want to re-invent the wheel. Perhaps something better than Nautilus-elementary could be developed; in the mean time, it exists, and too few people know about it.

---

### Post by KdotJ on 2010-08-15
> **libssd said:**
> 
People in *nix-land always want to re-invent the wheel. Perhaps something better than Nautilus-elementary could be developed; in the mean time, it exists, and too few people know about it.

Is a shame. I'm glad I found out about it, and will continue to use it... official repo or not.

@ ammonkey, thanks for the info. Understandable why it would be a big task to include it. However, I'm a little confused... You talk of the rewrite for other packages, but how come I can install it and use it with no issues? (Question, not a stab)

---

### Post by 23meg on 2010-08-15
> **KdotJ said:**
> To revive an old thread...

does anyone know if nautilus-elementary is going to make the repos for maverick??

In case you missed [the sticky thread]("http://www.ubuntuforums.org/showthread.php?t=1551557") here and the various announcements elsewhere, we're past [Feature Freeze]("https://wiki.ubuntu.com/FeatureFreeze"), after which new packages are not introduced into the archive (with the occasional minor exception of packages related to release goals).

If you want to keep up to date with the progress of the packaging, if any, simply subscribe to [the packaging request bug]("https://bugs.launchpad.net/ubuntu/+bug/585682").

---

### Post by KdotJ on 2010-08-15
> **23meg said:**
> In case you missed [the sticky thread]("http://www.ubuntuforums.org/showthread.php?t=1551557") here and the various announcements elsewhere, we're past [Feature Freeze]("https://wiki.ubuntu.com/FeatureFreeze"), after which new packages are not introduced into the archive (with the occasional minor exception of packages related to release goals).

If you want to keep up to date with the progress of the packaging, if any, simply subscribe to [the packaging request bug]("https://bugs.launchpad.net/ubuntu/+bug/585682").

Thank you 23meg for the info. Apologies for the lack of research on my part.

---

### Post by ammonkey on 2010-08-15
> **KdotJ said:**
> Is a shame. I'm glad I found out about it, and will continue to use it... official repo or not.

@ ammonkey, thanks for the info. Understandable why it would be a big task to include it. However, I'm a little confused... You talk of the rewrite for other packages, but how come I can install it and use it with no issues? (Question, not a stab)

because it replace the existing nautilus binaries, but as soon as the official nautilus package upgrade (idem est change version) it replace nautilus-elementary and vice et versa (if one version is superior to the other). The magic happens because nautilus-elementary have always a greater version than nautilus pakage.

Anyway it's a dead end, even if nautilus-elementary was a separate package, with differents libs/binaries, gnome don't offer any choice about the default filemanager. You need to tweak your conf to get a different filemanager like pcmanfm or thunar to work properly under gnome. And everytime nautilus would upgrade it would rewrite the configurations files.

To resume nautilus-elementary just can't be in official repo unless ubuntu choose to ship a different filemanager and ditch official nautilus package. It just won't happen. The discussion was up during UDS about enhancing nautilus with poor return like london hackfest was, like previous guadec was, seems no one really care about file managing ;) .. many discussions but no decisions as always.

---

### Post by KdotJ on 2010-08-16
Thank you for your reply, much appriciated. I must say I'm surprised that the discussion had poor return, but then nautilus does the job fine so I understand the decision not to change

---

### Post by libssd on 2010-08-16
Then I guess we'll just have to lobby for N-E functionality in Natty Newt, or whatever the release past Meerkat is named. Only 13 releases to go before the Roman alphabet runs out.

Re Ammonkey's comments, I obviously don't understand the politics (although I am quite familiar with developer egos and "not invented here"). Not an entirely rhetorical question: *Why can't the Nautilus and Elementary developers simply agree to merge functionality?* 

We're talking FOSS here, not development that involves $$$ property rights. If it's possible for an end user to do add Elementary after the fact, it can't be that difficult on a technical basis to make these features part of the base Nautilus distribution. Not including them puts the onus on the end user, who has to restore the missing functionality to Nautilus with every new release.

---

### Post by KdotJ on 2010-08-16
I guess it's a combo, or a few reasons i.e
The devs don't want to, this is FOSS as you said and money is not really a factor and perhaps is more effort than it's worth. 
It is only one of possibly many extensions/revamps out there. And let's be honey as stated before, nautilus elementary is one of those things you don't just stumble across and therefor I'm guessing in the big picture, not many people use it. 
I am however totally with you here, a merge would be fantastic, and judging by the poll in this thread, would be welcomed. 

As for the package replacement, I'm guessing an "official" nautilus update wil break my nautilus-elementary?

---

### Post by forcecore on 2010-08-17
Nautilus-elementary from ppa is most important thing to me, for example i have 10.04 custom .iso made with elementary. Default Nautilus is horrible compared to elementary, who needs those File Edit View... always rotting there. I do not care anymore of feature freezes after i found UCK - Ubuntu Customization Kit, without UCK Ubuntu is not perfect.

So end of topic and build custom .iso as you like.

---

### Post by ranch hand on 2010-08-17
I think you will find that, in most cases, remastersys is easier.

[http://ubuntuforums.org/showthread.php?t=1073838](http://ubuntuforums.org/showthread.php?t=1073838)

---

### Post by libssd on 2010-08-17
> **ranch hand said:**
> I think you will find that, in most cases, remastersys is easier.

[http://ubuntuforums.org/showthread.php?t=1073838](http://ubuntuforums.org/showthread.php?t=1073838)
I haven't tried UCK yet, but it appears to do slightly different things than remastersys (which is my default backup/restore tool, and has saved my bacon several times).

---

### Post by forcecore on 2010-08-18
Remastersys is causing lot of problems like losing installer from Ubuntu and causing login screen to appear and other problems, best thing is to edit .iso to get best results and UCK can only do this.

On topic: All who i installed edited Ubuntu (UCK) with Nautilus-elementary liked it loooot more than default "fat" Nautilus. Long live Elementary.

---

### Post by libssd on 2010-08-18
Other than problems caused by my own actions, Remastersys has never failed to create an image ISO from which I could not successfully restore. Ubuntu 9.04, 9.10, and 10.04.

---

### Post by snkiz on 2010-08-18
Why does everybody hate on tabs and split pane? I Use them all the time. The only ui disaster I see with them is as of 10.04 (Could have been 9.10) The tabs go all the way across the viewing area. makes it look really chunky. Split pane works well, just wish it would be more aware of where the mouse cursor is. But I guess the dev's don't like it, so obviously no one ever uses that feature right. Seems to me that nautilus has been part of gnome for too long. Just like the shell its dev's know best, and you use all of the environment or none of it.

---

### Post by berndth on 2010-09-10
> **snkiz said:**
> Split pane works well, just wish it would be more aware of where the mouse cursor is. But I guess the dev's don't like it, so obviously no one ever uses that feature right. Can you elaborate on that a bit more? Why should the panes be aware where the mouse cursor is?

---

### Post by scottuss on 2010-09-10
Personally I like Nautilus the way it is. I've used other, lesser, file managers and I always miss Nautilus.

---

### Post by snkiz on 2010-09-10
Its simple, the current setup in nautilus requires you to click somewhere in the file area of the pane to activate it, the toolbar does not do it. On my wish list would be to have nautilus switch panes whenever the mouse moves over the pane (including the toolbar.) with no click required.

---

