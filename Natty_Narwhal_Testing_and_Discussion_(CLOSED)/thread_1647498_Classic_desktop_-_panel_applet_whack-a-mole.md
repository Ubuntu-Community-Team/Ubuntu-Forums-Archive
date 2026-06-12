---
title: "Classic desktop - panel applet whack-a-mole"
date: 2010-12-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by pressureman on 2010-12-17
I'm running classic desktop since that's what I'm used to, and I'm giving Unity a bit longer to bake before I make my mind up whether I want to transition.

When I log into the classic desktop, most of the time, several panel applets (eg. trash, window list, show desktop, clock etc) fail to load, and a warning pops up, asking if I want to reload them. I click "reload", and there is then about a 50/50 chance that they will load successfully, or fail again. If I click "reload" often enough, I can usually get them all to eventually load.

I also notice that gnome-settings-daemon is sometimes failing to load, and my desktop goes back to 1998-styles :)

If I open a terminal and manually load gnome-settings-daemon, it comes back to normal.

I haven't seen any bugs or forum posts along these lines yet - am I the only one seeing them? This is a fresh install from natty-alternate-amd64, on Dec 14.

---

### Post by cecilpierce on 2010-12-17
> **pressureman said:**
> I'm running classic desktop since that's what I'm used to, and I'm giving Unity a bit longer to bake before I make my mind up whether I want to transition.

When I log into the classic desktop, most of the time, several panel applets (eg. trash, window list, show desktop, clock etc) fail to load, and a warning pops up, asking if I want to reload them. I click "reload", and there is then about a 50/50 chance that they will load successfully, or fail again. If I click "reload" often enough, I can usually get them all to eventually load.

I also notice that gnome-settings-daemon is sometimes failing to load, and my desktop goes back to 1998-styles :)

If I open a terminal and manually load gnome-settings-daemon, it comes back to normal.

I haven't seen any bugs or forum posts along these lines yet - am I the only one seeing them? This is a fresh install from natty-alternate-amd64, on Dec 14.

I see it to when triying to run classic desktop, hopefully it will be ironed out.

---

### Post by cariboo on 2010-12-17
I was getting the problem in both The Ubuntu Desktop and the Classic desktop, now I only have the problem with the Classic Desktop, so we are making progress. :)

---

### Post by kansasnoob on 2010-12-17
I can NOT guarantee your end-results so **proceed at you own risk, and be sure to read this all**!

I needed to track/test the progress of a few packages not related to the DE, and I thought about installing Xubuntu, but before doing so I went to Sys > Admin > Login Screen and set it to default to the classic desktop.

Next I removed these:

> Commit Log for Tue Dec  7 09:51:54 2010


Removed the following packages:
compiz-core
compiz-fusion-plugins-main
compiz-gnome
compiz-plugins
compizconfig-backend-gconf
libcompizconfig0
libdecoration0
ubuntu-desktop
unity


So far so good (with no desktop effects obviously), but today I notice that a partial-update wants to remove 'gnome-applets' and I suspect that would break the heck out of my Classic DE :D

That has to do with the update of the 'gir' packages:

> gir1.0-atk-1.0 will be removed
gir1.0-freedesktop will be removed
gir1.0-gconf-2.0 will be removed
gir1.0-gdkpixbuf-2.0 will be removed
gir1.0-glib-2.0 will be removed
gir1.0-gtk-2.0 will be removed
gir1.0-gtk-3.0 will be removed
gir1.0-panelapplet-3.0 will be removed
gir1.0-pango-1.0 will be removed
............................
gir1.2-freedesktop (version 0.9.12+git20101124-0ubuntu5) will be installed
gir1.2-gconf-2.0 (version 2.32.1-1ubuntu2) will be installed
gir1.2-gdkpixbuf-2.0 (version 2.22.1-0ubuntu5) will be installed
gir1.2-glib-2.0 (version 0.9.12+git20101124-0ubuntu5) will be installed
gir1.2-pango-1.0 (version 1.28.3-3) will be installed

So I'll wait at least a couple of days to see if that resolves itself.

---

### Post by Harry33 on 2010-12-17
> **kansasnoob said:**
> 
...
That has to do with the update of the 'gir' packages:
So I'll wait at least a couple of days to see if that resolves itself.

Yes that is the transition from gir1.0 to gir1.2.
You need to install new packages:
gtk+2.0
gtk+3.0
gnome-panel
gnome-applets
pygobject
After that the gir packages are changed too.

These all have been available from the main server for some time now.

---

### Post by mc4man on 2010-12-17
Actually have no real current issue w/ a Desktop login to unity and a Classic login to gnome-panel w/ basic panel applets, compiz ect.

You need to set your ccsm up separately for each, ie. set Desktop compizconfig appropriate to unity, classic compizconfig appropriate to gnome-panel.
( there are, for lack of better description, separate 'profiles' per login

---

### Post by kansasnoob on 2010-12-17
> **Harry33 said:**
> Yes that is the transition from gir1.0 to gir1.2.
You need to install new packages:
gtk+2.0
gtk+3.0
gnome-panel
gnome-applets
pygobject
After that the gir packages are changed too.

These all have been available from the main server for some time now.

Good to know, thank you :)

---

### Post by kansasnoob on 2010-12-17
> **mc4man said:**
> Actually have no real current issue w/ a Desktop login to unity and a Classic login to gnome-panel w/ basic panel applets, compiz ect.

You need to set your ccsm up separately for each, ie. set Desktop compizconfig appropriate to unity, classic compizconfig appropriate to gnome-panel.
( there are, for lack of better description, separate 'profiles' per login

That makes a lot of sense. That makes much more sense than what I did ;)

OT, but so far I really like the general "looks" of Unity (bugs aside) on my wide-screen. It just makes better use of real estate.

OTOH it's a kludge on my old 17" CRT which actually measures about 15.5" diagonal. Obviously the Unity desktop is not going to work for everyone, but I think they're aware of that and dealing with it in an appropriate manner.

---

### Post by mc4man on 2010-12-17
There are from what I see atm 3 possibilities - 
Desktop Edition > unity
Classic > gnome-panel
Classic > unity

While the third is viable it will cause issues if then  trying to do the second one - better to deal with unity issues/settings from the Desktop login.

Also a factor atm is the [last update to compiz]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/690461") - it [needs to be addressed]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/691403") and is the possible cause of Desktop login to spinning icon or people finding they need to alternate logins to get a successful Desktop > unity login

All of this is not to say that the login to either is completely stable, but in any case where something goes south here a simple logout/in resolves
(for the most part I'm only using Desktop > unity

---

### Post by pressureman on 2011-01-09
Bumping this thread, curious if other people are still experiencing it. I was hoping that it might have fixed itself by now, as part of some other update.

Hopefully Gnome classic desktop isn't always going to be treated like a second class citizen, now that everybody is drooling over Unity.

---

### Post by amano on 2011-01-09
Where is the bug report for that issue?

---

### Post by pressureman on 2011-01-09
> **amano said:**
> Where is the bug report for that issue?

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/676624](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/676624)

---

### Post by jerrynewt on 2011-01-09
Same problem here (Classic Desktop), all applets are having to be reloaded at every boot, but not all come back every time. Opened .xsession-errors and at the end of the log it says to have administrator enable user sharing. How would I accomplish this?? I am the only user on this laptop.

---

### Post by pressureman on 2011-01-10
I think your error messages about enabling user sharing are unrelated.

Remember that ~/.xsession-errors logs errors/warnings from all X apps, not just gnome-panel ;-)

---

### Post by scradock on 2011-01-10
> **pressureman said:**
> Bumping this thread, curious if other people are still experiencing it. I was hoping that it might have fixed itself by now, as part of some other update.

Hopefully Gnome classic desktop isn't always going to be treated like a second class citizen, now that everybody is drooling over Unity.
I get this sometimes, on Maverick as well, and also (often) find that the panels don't show when I start Maverick or Natty (classic). It seems to be a timing issue - some part of the session gets ahead of itself and loads wallpaper and apps before the panel, which then stays hidden. I keep a launcher on the desktop to "pkill gnome-panel", which then re-spawns, but doesn't bring up my weather applets.....

Logging out and in again usually fixes the problem, but it's quicker to get a panel using the launcher.

---

### Post by scradock on 2011-01-10
> **pressureman said:**
> Bumping this thread, curious if other people are still experiencing it. I was hoping that it might have fixed itself by now, as part of some other update.

Hopefully Gnome classic desktop isn't always going to be treated like a second class citizen, now that everybody is drooling over Unity.

I get this sometimes, on Maverick as well, and also (often) find that the panels don't show when I start Maverick or Natty (classic). It seems to be a timing issue - some part of the session gets ahead of itself and loads wallpaper and apps before the panel, which then stays hidden. I keep a launcher on the desktop to "pkill gnome-panel", which then re-spawns, but doesn't bring up my weather applets.....

Logging out and in again usually fixes the problem, but it's quicker to get a panel using the launcher.

---

### Post by OliW on 2011-04-20
Also suffering this from a recent Maverick "upgrade". The menu is practically the only applet available. Useful things like the WindowListApplet are nowhere to be seen.

I'll admit I didn't understand the earlier posts about removing compiz packages. Is there something that can be done to get this working? I'm not sure I'll survive another day without a window list.

---

### Post by kansasnoob on 2011-04-20
> **OliW said:**
> Also suffering this from a recent Maverick "upgrade". The menu is practically the only applet available. Useful things like the WindowListApplet are nowhere to be seen.

I'll admit I didn't understand the earlier posts about removing compiz packages. Is there something that can be done to get this working? I'm not sure I'll survive another day without a window list.

Are you using the classic desktop or Unity? I've found almost all applets to work with classic and classic w/o effects since we're still using Gnome version 2.32.

---

### Post by OliW on 2011-04-20
> **kansasnoob said:**
> Are you using the classic desktop or Unity? I've found almost all applets to work with classic and classic w/o effects since we're still using Gnome version 2.32.

Classic desktop with Compiz.

---

