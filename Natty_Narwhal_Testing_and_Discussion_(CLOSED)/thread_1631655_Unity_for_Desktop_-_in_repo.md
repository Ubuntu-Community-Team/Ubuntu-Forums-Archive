---
title: "Unity for Desktop - in repo"
date: 2010-11-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by scradock on 2010-11-26
I just updated and got the new compiz-unity packages from the repo. I hope it's appropriate to start a new thread for those who didn't compile it themselves, but have questions and comments about the current epiphany.

First: I like it! It seems neat and clean, and I'm prepared to continue using it.

second: I have an older (read "legacy") machine with ATI Radeon Xpress 200M graphics, using OS drivers, and this version seems to work as far as basic desktop layout goes.

third: main initial problem is that the black "top bar" covers and nullifies my top panel, which has ALL functionality (App menu, Sys menu, places menu, applets, etc etc etc) Curious choice - I see some applets are replaced in the black bar, but no sign of menus. For now I've added a "Gnome menu" to the BOTTOM panel, which remains intact.

fourth: first time I started it, nm-applet didn't start, so no Internet connection. No problem, except that with (third) above there was no obvious place to run anything from.

fifth: Tomboy in the left launcher - how do I remove it? It is no doubt a fine app for those who want it, but i don't.

sixth (and final for now): where are the instructions? "man unity" gives nothing.... this is Linux, for heaven's sake - there are standard protocols for issuing information......

HTH

---

### Post by cariboo on 2010-11-26
Remember, you're using pre-alpha software.

> third: main initial problem is that the black "top bar" covers and nullifies my top panel, which has ALL functionality (App menu, Sys menu, places menu, applets, etc etc etc) Curious choice - I see some applets are replaced in the black bar, but no sign of menus. For now I've added a "Gnome menu" to the BOTTOM panel, which remains intact.

There will be a global menu now, places and system, haven't been implemented yet

> fourth: first time I started it, nm-applet didn't start, so no Internet connection. No problem, except that with (third) above there was no obvious place to run anything from.

There isn't an nm-applet that works with this version of Unity yet, see bug# [lpbug]680298[/lpbug]

```
sixth (and final for now): where are the instructions? "man unity" gives nothing.... this is Linux, for heaven's sake - there are standard protocols for issuing information......
```

There isn't any as yet, see the first sentence. For help I would suggest posting in the [Unity technical thread]("http://ubuntuforums.org/showthread.php?t=1624082")

---

### Post by scradock on 2010-11-27
> **cariboo907 said:**
> Remember, you're using pre-alpha software.



There will be a global menu now, places and system, haven't been implemented yet



There isn't an nm-applet that works with this version of Unity yet, see bug# [lpbug]680298[/lpbug]

```
sixth (and final for now): where are the instructions? "man unity" gives nothing.... this is Linux, for heaven's sake - there are standard protocols for issuing information......
```

There isn't any as yet, see the first sentence. For help I would suggest posting in the [Unity technical thread]("http://ubuntuforums.org/showthread.php?t=1624082")

Well, thanks for all the details - good to know. But I still think that the UTT is a bit - shall we say "technical"? - for those of us who enjoy trying things out when they have been released through the repos but would be wary of ppas and such-like, let alone compiling for ourselves....

---

### Post by cariboo on 2010-11-27
I would suggest, if you really want to try Unity, you wait until at least the Beta release. there are going to be quite a few changes between now and the end of March. The main thrust is to get a working version of Unity with very few features ready for the first alpha release.

---

### Post by scradock on 2010-11-27
> **cariboo907 said:**
> I would suggest, if you really want to try Unity, you wait until at least the Beta release. there are going to be quite a few changes between now and the end of March. The main thrust is to get a working version of Unity with very few features ready for the first alpha release.

That's no doubt well-meant, but not advice I shall take. I enjoy trying out the new ideas as they emerge, and even pick up and report the occasional bug to help things along. I just don't rush ahead of the repos too much, as I prefer to have some hope of basic functionality to start with.

I've been watching the action over on the technical thread, and your Q&A sticky, and felt the one was too focused on bleeding-edge stuff that wasn't working yet, and the other was mainly focused on future hopes. Well, now we have something that basically works, on my old laptop, and I hoped to start a thread for people to discuss it as it evolves.

---

### Post by cariboo on 2010-11-27
I usually look at the user details to the left, I see you haven't told use what version your using, so I assumed you were just trying Unity and were disappointed that it didn't work very well yet. 

Welcome, we can use all the testers we can get. One word of advice I have is to report your Unity bugs directly to the developers at [https://bugs.launchpad.net/unity]("https://bugs.launchpad.net/unity"), you can still enter bugs manually, and for me at least I seem to get a faster response from the development team.

---

### Post by autocrosser on 2010-11-27
I have started another bug: [https://bugs.launchpad.net/unity/+bug/682215](https://bugs.launchpad.net/unity/+bug/682215)

Moving multiple files in the Unity install causes my system to slow to a crawl....This is with a i7-940 system with 2T worth of 7200rpm SATA2 drives......Seems that Nautilus is not liking Unity.......

---

### Post by scradock on 2010-11-27
> **cariboo907 said:**
> I usually look at the user details to the left, I see you haven't told use what version your using, so I assumed you were just trying Unity and were disappointed that it didn't work very well yet. 

Welcome, we can use all the testers we can get. One word of advice I have is to report your Unity bugs directly to the developers at [https://bugs.launchpad.net/unity]("https://bugs.launchpad.net/unity"), you can still enter bugs manually, and for me at least I seem to get a faster response from the development team.

OK, I put mine in my sig - have been using testing versions since hardy. 

I tried to make it clear that I am not disappointed; I have dipped my toe in a couple of times already and retreated when Unity didn't work in my laptop. Now I'm impressed that it works as well as it does. But there is perhaps a need for a place where we can help each other with quick fixes when things aren't yet fully operational......

For instance, I have learned how to go beyond the default gnome2 "top and bottom panels" comfort zone and added a single (short, hideable) top panel for the Gnome menu-bar, at least until Unity has the appmenu enabled. That way I have access to applications and system controls...

This is what I'm here for - small puzzles that I can solve, hopefully to help others as well.

I haven't run into anything that I would call a "bug" yet, apart from the fact that compiz tends to fall over when some of the plugins are turned on or off, or even edited from cfcm - but I see that others have already reported that.

---

