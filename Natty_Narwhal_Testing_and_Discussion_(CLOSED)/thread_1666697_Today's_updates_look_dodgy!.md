---
title: "Today's updates look dodgy!"
date: 2011-01-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-01-14
7 of today's updates don't want to install because of a dependency that is not to be installed yet.
The compiz updates want to remove Unity! That looks dodgy! I think I'll wait and see :-)

---

### Post by kyleabaker on 2011-01-14
[http://ubuntuforums.org/showpost.php?p=10353717&postcount=133](http://ubuntuforums.org/showpost.php?p=10353717&postcount=133) me too ;)

---

### Post by dino99 on 2011-01-14
no issue here: none of compiz or unity installed :)

---

### Post by Quackers on 2011-01-14
> **dino99 said:**
> no issue here: none of compiz or unity installed :)

You're a bad man :-)

---

### Post by ronacc on 2011-01-14
I've got compiz but I disabled unity on first boot , I can't update for another 2 days or so anyway , I've got mkfs.ext3 running with the -cc option on a 320 gb drive , 8 hrs in its 12% done .

---

### Post by Quackers on 2011-01-14
I don't understand what you said, but I understand the implications :-)
Your hard drive will wear out!

---

### Post by ronacc on 2011-01-14
I'm trying to salvage that drive , it seems to have got messed up during an install of another distro that went bad . mkfs.ext3 creates an ext3 file system on the drive , the -c option tests for bad blocks and marks them out , -cc uses a destructive read/write test to do it ( a more stringent test). but it is slow .

---

### Post by Quackers on 2011-01-14
Ah I see, thanks. Pretty intensive then. Lots of disk chatter going on :-)

---

### Post by rburkartjo on 2011-01-14
same problem here lots of dependencies missing and wont do a partial. getting all i can with safe upgrade

---

### Post by madjr on 2011-01-14
same here, updates have gone crazy.

i thought i was going to get a complete unity today, but instead it wants to remove it (and probably break the whole thing)... glad i didn't do it.

But i still wonder how the devs let this stuff happen in the first place. bad bad

---

### Post by ronacc on 2011-01-14
when lots of updates are hitting this happens sometimes , thats why you should always look over what it wants to do before pulling the trigger . much easier on the toes that way:P

---

### Post by jfernyhough on 2011-01-14
I always use synaptic for my updates, especially for the early alphas. This way I can see exactly which packages are being updated, go through them one at a time, and I have the option of ignoring nasty-looking changes (like grub, initram and xserver updates).

---

### Post by OGpmpdog on 2011-01-14
> **jfernyhough said:**
> I always use synaptic for my updates, especially for the early alphas. This way I can see exactly which packages are being updated, go through them one at a time, and I have the option of ignoring nasty-looking changes (like grub, initram and xserver updates).

+1, Update Manager should be DISABLED during development cycle updates.

---

### Post by OGpmpdog on 2011-01-14
> **jfernyhough said:**
> I always use synaptic for my updates, especially for the early alphas. This way I can see exactly which packages are being updated, go through them one at a time, and I have the option of ignoring nasty-looking changes (like grub, initram and xserver updates).

+1, Update Manager should be DISABLED during development cycle updates.

---

### Post by Quackers on 2011-01-14
Me too, that's how I noticed this.
I've now installed the compiz updates, as a new Unity apepared in the upgrades. Not restarted yet though :-)
There are still about 10 updates left, waiting for libwebgtk something or other.

---

### Post by mc4man on 2011-01-14
> +1, Update Manager should be DISABLED during development cycle updates.
That's a rather silly thing to say, the update manager is very useful at any time inc. dev cycle
It shows ALL the updated packages with descriptions, changes and active links to bug reports when applicable
It will also never install packages with dependency issues unless when accepts the partial pop up which there is no reason to do.

> waiting for libwebgtk something or other
Those libs have been available for a while (needed for banshee and empathy updates ect.
It may be that you'll need to open synaptic and manually mark libwebkitgtk-1.0-common for install to move along if waiting doesn't clear up.

---

### Post by Quackers on 2011-01-14
dodgy double post

---

### Post by Quackers on 2011-01-14
> **mc4man said:**
> 

Those libs have been available for a while (needed for banshee and empathy updates ect.
It may be that you'll need to open synaptic and manually mark libwebkitgtk-1.0-common for install to move along if waiting doesn't clear up.

I have installed libwebkitgtk-1.0-common and it solved some update non-starters, thanks.
However all the updates left to run want to remove unity or cairo dock, but its replacement won't install, due to these dependencies
```
unity:
 Depends: libindicator2 but it is not going to be installed
  Depends: unity-common (=3.2.8-0ubuntu3) but 3.2.8-0ubuntu1 is to be installed
 Recommends: unity-place-applications but it is not going to be installed
 Recommends: unity-place-files but it is not going to be installed
 Recommends: indicator-messages but it is not going to be installed
 Recommends: indicator-me but it is not going to be installed
 Recommends: indicator-session but it is not going to be installed


```
Should I look through synaptic for all those packages first? Or won't they be there yet?
I know from my other Natty, that if I allow unity to be removed, the new one will not install. That installation's a bit messy now :-)

---

### Post by tekstr1der on 2011-01-14
> **mc4man said:**
> [QUOTE=OGpmpdog;10357455]+1, Update Manager should be DISABLED during development cycle updates.

That's a rather silly thing to say, the update manager is very useful at any time inc. dev cycle
It shows ALL the updated packages with descriptions, changes and active links to bug reports when applicable
It will also never install packages with dependency issues unless when accepts the partial pop up which there is no reason to do.[/QUOTE]

Indeed that's absolutely silly! The Update Manager itself receives updates that require testing throughout the dev cycle. Nothing like releasing a broken Update Manager to the masses because it was never tested.

---

### Post by madjr on 2011-01-14
> **OGpmpdog said:**
> +1, Update Manager should be DISABLED during development cycle updates.

just saying that synaptic wanted to remove ubuntu-desktop, unity and compiz this morning.... so is not the safe choice either.

i think that dangerous updates should be on their own ppa just for the developers to break their own stuff and not everyone elses

---

### Post by tekstr1der on 2011-01-14
Deleted

---

### Post by tekstr1der on 2011-01-14
> **mc4man said:**
> [QUOTE=OGpmpdog;10357455]+1, Update Manager should be DISABLED during development cycle updates.

That's a rather silly thing to say, the update manager is very useful at any time inc. dev cycle
It shows ALL the updated packages with descriptions, changes and active links to bug reports when applicable
It will also never install packages with dependency issues unless when accepts the partial pop up which there is no reason to do.[/QUOTE]

Indeed that's absolutely silly! The Update Manager itself receives updates that require testing throughout the dev cycle. Nothing like releasing a broken Update Manager to the masses because it was never tested because it was DISABLED.

---

### Post by tekstr1der on 2011-01-14
What the heck is happening with my post? Mod please delete my double, triple posts? On my end it never posted, just sat and spun.

Sorry!

---

### Post by jennybrew on 2011-01-14
Awesome updates :)
It certainly looked as if Synaptic wanted to remove all the desktop so I chickened out.
Update Manager, as far as I could tell was all set to strip out Compiz manager and Unity too.
Maybe Monday will be better :)

---

### Post by mc4man on 2011-01-14
> Maybe Monday will be better
possibly before than - 
the new unity source package is 3.2.12 though I'd say the odds are it's going to fail to build as it is now (did here on some nux errors.
If so then some adjustments will need to happen..

---

### Post by Quackers on 2011-01-14
I made this post over an hour ago, but it seems to have got lost!
I installed the lib package that you suggested, mc4man, and it did allow some updates to run, thanks :-)
However all of the updates left to run want to remove Unity or cairo dock. And I know from my other Natty install (which is now in a bit of disarray :wink: ) that neither the new Unity or Cairo dock will install due to several dependency issues.
So I'm awaiting further developments :-)

---

### Post by Harry33 on 2011-01-14
> **Quackers said:**
> 
...
```
unity:
 Depends: libindicator2 but it is not going to be installed
  Depends: unity-common (=3.2.8-0ubuntu3) but 3.2.8-0ubuntu1 is to be installed
 Recommends: unity-place-applications but it is not going to be installed
 Recommends: unity-place-files but it is not going to be installed
 Recommends: indicator-messages but it is not going to be installed
 Recommends: indicator-me but it is not going to be installed
 Recommends: indicator-session but it is not going to be installed

```
...


I use main server repositories, and these packages are all available:
- libindicator2_0.3.16-0ubuntu1
- unity-common_3.2.8.-0ubuntu3
- unity-place-applications_0.2.26-0ubuntu2
- unity place-files_0.5.32-0ubuntu1
- indicator-messages_0.3.11-0ubuntu4
- indicator-me_0.2.11-0ubuntu1
- indicator-session_0.2.11-0ubuntu1

Try synaptic, it is a lot better and safer with more info.

BTW unity_3.2.12-0ubuntu1 is currently building (64-bit):
[https://launchpad.net/ubuntu/natty/+source/unity/3.2.12-0ubuntu1](https://launchpad.net/ubuntu/natty/+source/unity/3.2.12-0ubuntu1)

---

### Post by kyleabaker on 2011-01-14
> **Quackers said:**
> I made this post over an hour ago, but it seems to have got lost!

The ubuntuforums.org servers seem to be having a terrible time keeping up this week. I've had several problems posting here myself and I'm seeing a lot of duplicate posts from others as well. Wish they would fix that!

I'm also waiting on the last few updates so as to not remove Unity. :popcorn:

---

### Post by Quackers on 2011-01-14
> **Harry33 said:**
> I use main server repositories, and these packages are all available:
- libindicator2_0.3.16-0ubuntu1
- unity-common_3.2.8.-0ubuntu3
- unity-place-applications_0.2.26-0ubuntu2
- unity place-files_0.5.32-0ubuntu1
- indicator-messages_0.3.11-0ubuntu4
- indicator-me_0.2.11-0ubuntu1
- indicator-session_0.2.11-0ubuntu1

Try synaptic, it is a lot better and safer with more info.

BTW unity_3.2.12-0ubuntu1 is currently building (64-bit):
[https://launchpad.net/ubuntu/natty/+source/unity/3.2.12-0ubuntu1](https://launchpad.net/ubuntu/natty/+source/unity/3.2.12-0ubuntu1)

Thanks Harry33, but if they're available what's the problem? Why doesn't synaptic know that they're available and install them with the package that depends on them? I am using synaptic for updates (I learned that a while ago :wink: :-)  )

---

### Post by mc4man on 2011-01-14
You should see the newer builds soon, the libnux libraries were updated and the .12 version of unity can or has been built
(have  .12 installed here, though a restart is needed to see...

Edit: not quite ready for 'prime time', works okay but do see an issue or two...

---

### Post by Harry33 on 2011-01-14
> **Quackers said:**
> Thanks Harry33, but if they're available what's the problem? Why doesn't synaptic know that they're available and install them with the package that depends on them? I am using synaptic for updates (I learned that a while ago :wink: :-)  )

Are you using the main server. For example Finnish and Swedish servers it takes one day more have the updates.

---

### Post by Quackers on 2011-01-14
I was using the server for the UK, but I've changed to the main server now. Update Manager reported a partial upgrade available, but I don't want that :-)
I'll go and check on any changes in synaptic and get back to you.

---

### Post by Quackers on 2011-01-14
No apparent changes in dependencies so far.
I'll go through synaptic looking for all the dependencies one by one and try it that way.

No, that's just more of the same. You find one and it wants to remove Unity to install itself.
There is a unity update in with the updates, but that's version 3.2.8-0ubuntu3, but that won't install either :-)

---

### Post by plun on 2011-01-14
Well... packages are just broken for the moment !!!

```
The following packages have unmet dependencies:
 ubuntu-desktop : Depends: indicator-applet-session but it is not going to be installed
                  Depends: unity but it is not going to be installed
E: Broken packages

```

Just normal testing  !!

---

### Post by mc4man on 2011-01-14
Just wait it out..
can say there are some interesting things w/ .12, possibly when it's available on servers it won't show all. 

Some windows open maximized, there was some mention of that in changelog, hopefully just a temp or local thing
All windows have a bit of transparency - sorta weird 
All the launcher icons have their 'backgrounds' exposed like when the app is open  - did see that in the bzr a week ago so probably not unknown (is an option in unity plugin

Wireless did crash on several logins, though good now

Edit: actually the transparency is only when you 'grab' a window - which is ok (though they do 'slide' a bit

---

### Post by Quackers on 2011-01-14
I'll look forward to it then :-)

---

### Post by mc4man on 2011-01-14
Turns out the 'backlight' on launcher icons is an option in the unity plugin, it's enabled by default and can be turned off (in experimental section

After a few restarts the max'ed windows are now only some, though more on a laptop than a desktop (which is good

---

### Post by seeker5528 on 2011-01-14
> **madjr said:**
> just saying that synaptic wanted to remove ubuntu-desktop, unity and compiz this morning.... so is not the safe choice either.

If you go to 'Settings --> Preferences --> General' and verify that 'System Upgrade:' is set to 'Default Upgrade', clicking the 'Mark All Upgrades' button is just as safe as doing 'apt-get upgrade' or 'aptitude safe-upgrade'. I would consider it safer than 'aptitude safe-upgrade' since aptitude keeps a list of some things it considers safe in addition to what would be install by apt-get or synaptic.

If you are individually selecting packages, it doesn't matter which method you use, it's up to you to verify and confirm that any packages listed as packages that will be removed are packages you actually want to allow to be removed.

I have not used update manager for a while, but I am pretty sure that when I did, every time it wanted to do a partial install it offered me a choice about whether to allow the partial install or not.

If you choose to play, you take your chances, that's what it means to use an unstable product. Any time there is an ABI change there is potential the not all the affected packages will make it into the archives in a short time of each other and/or some affected packages may not even get rebuilt for a while.

Later, Seeker

---

### Post by Quackers on 2011-01-14
Aha! Good news :-)
All updates have now run successfully :-)
Unity 12 or whatever it's called :wink: is now installed and I have the backlit icons. 
The only slight downsides appear to be a re-ordering of some top panel applets and a decidedly stunted cairo dock (which is a surprise, as cairo dock seems to have been removed! ). Half my icons are missing and some stilted effects, but all in all not bad at all. I'll keep a lookout for cairo dock updates :-)

Now I can have a go at fixing the other Natty install!

Excellent, now that's back up too :-)  No cairo dock at all on this one but nevermind :-)

---

### Post by ratcheer on 2011-01-14
Thanks, Quackers. I will go and try again. The last time I tried, I got about 30 held updates.

Tim

---

### Post by Quackers on 2011-01-14
Have fun :-)

---

### Post by ratcheer on 2011-01-14
> **Quackers said:**
> Have fun :-)

No joy. It downloaded 6 package updates and only installed 4 of them. I now have 32 held updates: 14 Gnome, 7 libs, 1 Misc, 2 Python, 2 Sound, and 6 X11.

I'm not sure what, if anything, I'm supposed to do to resolve all the interdependencies.

Tim

---

### Post by Quackers on 2011-01-14
I changed to the main server, from the server for the UK. Which are you on?

---

### Post by Universal344 on 2011-01-14
Try updating through synaptic.  It had to remove a bunch of old unity packages (the unity places, libunity0 and libindicator2) and then it ran fine.  Just make sure its installing/updating the newer versions of those packages (with the exception of the unity places because we'll be getter new versions of those later on).

---

### Post by ratcheer on 2011-01-14
> **Quackers said:**
> I changed to the main server, from the server for the UK. Which are you on?

I have no idea - just however it comes. Main, I guess.

Tim

---

### Post by Quackers on 2011-01-14
I'm using synaptic, as Universal344 suggested, did you?
The server choice is in the settings (bottom left) of the Update Manager Window (can't remember which tab, first I think).

---

### Post by cariboo on 2011-01-14
You can also open Main Menu, in the Applications window, and enable Software Sources under the System->Administration menu.

---

### Post by Quackers on 2011-01-15
Blimey, 12 hours later and there's a newer version of unity, again!

---

### Post by ratcheer on 2011-01-15
> **Quackers said:**
> I'm using synaptic, as Universal344 suggested, did you?
The server choice is in the settings (bottom left) of the Update Manager Window (can't remember which tab, first I think).

No, I have made it a habit always to use aptitude.

Tim

---

### Post by ratcheer on 2011-01-15
Ok, I got everything installed with Synaptic. I suppose aptitude was just "playing it safe".

Thanks.

Tim

---

### Post by Quackers on 2011-01-15
I've found that synaptic will run updates that aptitude won't. I was wondering if I was doing it wrong :-) Maybe it was just being ultra safe.

---

### Post by ratcheer on 2011-01-15
> **Quackers said:**
> I've found that synaptic will run updates that aptitude won't. I was wondering if I was doing it wrong :-) Maybe it was just being ultra safe.

I think so. The standard Ubuntu Update Manager said it would have to do a partial upgrade. I imagine that by accepting the solution proposed by Synaptic, we were doing that partial upgrade.

Tim

---

### Post by ronacc on 2011-01-15
synaptic seems to have better conflict/dependency resolution than update manager , I often find that it will update things that a partial upgrade won't .

---

### Post by efflandt on 2011-01-15
I had not done updates with Update Manager since 2011-01-13  16:24:19 CST (-6:00) due to some of these posts.  After those updates Unity and top panel would crash when logging on, but seemed to work fine after **sudo restart gdm** from console.

But I just used Synaptic > Custom Filters > Upgradable (upstream) and Mark all upgrades, and after rebooting everything "seems" to be working.  Firefox full screen window controls and title are now integrated into top panel, although it still has its own menu bar.

---

### Post by SushiR on 2011-01-15
For everybody who feels safe with some work in terminal (which I assume if you're running an alpha version of Ubuntu), I strongly recommend using aptitude. With following commands you update you're system without messing the system up with unmet dependencies hell

```
sudo aptitude update && sudo aptitude safe-upgrade
```

But please don't forget, that (as for now) every update can bork your system. But that's usual business for development releases.

---

### Post by Quackers on 2011-01-15
On one install I have no cairo dock at all. On this install I have a small cairo dock, which is surprising as cairo dock has been removed during updates, due to dependencies. It still works as well :-) although some of it is missing. Very odd!
The first of the cairo dock upgrades has arrived :-)  though not cairo dock program itself  :-(  Won't be long, hopefully.
I like cairo dock, because when Unity fails, it is the only way I can fix things.
Alt + F2 and ctrl + Alt + T don't work any more here.

---

### Post by Quackers on 2011-01-15
duplicate

---

### Post by nm_geo on 2011-01-15
> **efflandt said:**
> I had not done updates with Update Manager since 2011-01-13  16:24:19 CST (-6:00) due to some of these posts.  After those updates Unity and top panel would crash when logging on, but seemed to work fine after **sudo restart gdm** from console.

But I just used Synaptic > Custom Filters > Upgradable (upstream) and Mark all upgrades, and after rebooting everything "seems" to be working.  Firefox full screen window controls and title are now integrated into top panel, although it still has its own menu bar.

I just did the same and everything is working well.  The application icons are looking much nicer very improved, and I have filled the Unity panel to the brim by pinning sixteen icons to it.  I like that smashed trash look.

---

### Post by nm_geo on 2011-01-15
Duplicate took 5 minutes to get posted

---

### Post by coffeecat on 2011-01-15
> **SushiR said:**
> For everybody who feels safe with some work in terminal (which I assume if you're running an alpha version of Ubuntu), I strongly recommend using aptitude.

I was happy using aptitude safe-upgrade until this morning when it broke Unity. But I was able to mend it again with an update from Synaptic this evening. Maybe a special case, but I think it's not just a case of ymmv, it's ymmv  according to what time and day you try to vary your mileage. :?

> **SushiR said:**
> But please don't forget, that (as for now) every update can bork your system.

Agreed.

---

### Post by ratcheer on 2011-01-15
> **SushiR said:**
> For everybody who feels safe with some work in terminal (which I assume if you're running an alpha version of Ubuntu), I strongly recommend using aptitude. With following commands you update you're system without messing the system up with unmet dependencies hell

```
sudo aptitude update && sudo aptitude safe-upgrade
```But please don't forget, that (as for now) every update can bork your system. But that's usual business for development releases.

That is what I always do, but Natty was building up a large backlog of held updates doing it that way. As suggested by others, I tried Synaptic and the conflicts were resolved.

Tim

---

