---
title: "Problem updating from 10.04 to 10.10 Beta"
date: 2010-09-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by HistoryMac on 2010-09-03
Hey all,
I just got word that the beta release of 10.10 was out and decided pretty quickly that I was going to try it out. I'm running 10.04 at the moment, so hit Alt+F2 and ran "update-manager -d" and hit the upgrade button for 10.10. Every goes well enough, until it gets to "Setting new software channels" which, upon completing, returns this error:

```
 
An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

```

Anyone else have (or have a solution to) this problem?

---

### Post by Mark Phelps on 2010-09-03
Yeah -- such questions related to Alpha/beta versions of Ubuntu belong in the appropriate Development forum, not here.

If you're going to mess around with pre-release versions, especially Alphas, you need to be closely monitoring the right forum.

Will be asking the Mods to move this thread there.

---

### Post by cariboo on 2010-09-04
Moved to maverick testing and discussion.

---

### Post by VMC on 2010-09-04
> **HistoryMac said:**
> Hey all,
I just got word that the beta release of 10.10 was out and decided pretty quickly that I was going to try it out. I'm running 10.04 at the moment, so hit Alt+F2 and ran "update-manager -d" and hit the upgrade button for 10.10. Every goes well enough, until it gets to "Setting new software channels" which, upon completing, returns this error:

```
 
An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

```

Anyone else have (or have a solution to) this problem?

Please read the stickies, specifically this [one]("http://ubuntuforums.org/showthread.php?t=1479146") regarding partial upgrades. You may have committed when you shouldn't have. I don't use Update Manager and have never used the upgrade feature.

---

### Post by ranch hand on 2010-09-04
I just checked the beta test results and if you have a 64bit OS it does not look good on the Update Mangler upgrade.

32bit faired a little better.

I do not upgrade that way but UM is the recommended route by Ubuntu.

If you can get to a terminal you could use the old (not recommended by Ubuntu) Debian upgrade path.

You need to check your /etc/apt/sources.list and make sure that all instances of lucid are replaced by maverick.  Comment out all ppas (check sources.list.d too) and non-Ubuntu repos.  Uninstall non OSS drivers.  These things can be put back after the upgrade but it will be smoother (even using UM) if they are not in the mix.

Run;
```

sudo apt-get update

```
and then;
```

sudo apt-get dist-upgrade

```
when it is finished run;
```

sudo dpkg --configure -a

```
several times until;
A>it comes up clean
B>it makes no more progress

Then reboot to recovery and run the "dpkg fix broken packages" option.  All this dpkg stuff is what UM does in the final stage that it refers to as "clean up".

Then choose "return to normal boot".

When you log in and get the next prompt, type   startx  this should take you to the desktop.

Updating (questionable term when going from stable to unstable) is kind of a crap shoot.  Do read the stickies, at least the first post of each.

Do not rush.  Think it through.

It is, at this point, not too late to come to your senses and wait a few weeks for the RC or Final.

---

### Post by 23dornot23d on 2010-09-04
After you have the Maverick Source files in etc/apt/sources.list  ....... probably will be already there but if
you do as ranch hand says first ...... the apt-get dist-upgrade ...... should pull them in.

[COLOR=Blue][B]The one thing that has saved my system many times is to do
[/B][/COLOR] 
sudo apt-get update

sudo apt-get install aptitude

[COLOR=Blue]I prefer aptitude as this saved my systems many times in the past and from some pretty dire situations.[/COLOR]

sudo aptitude update

sudo aptitude safe-upgrade

It tends to give you some useful information back to you the user on your chances of repairing your SYSTEM.

( But it all depends on how borked up it is .... [COLOR=Red]if configuration files go missing for networks and the likes then you may have problems and the quickest thing to do sometimes is a clean install in another partition[/COLOR] and then pull across all the files you need to save in the new one - OR make a separate /home then next time there are not as many worries about losing your data . )

and as Ranch Hand says ....... keep trying it day after day ....... each day new programs and fix's are released. 36 days to the final release so it should get a lot better the closer it gets to the 10.10.2010.

---

### Post by HistoryMac on 2010-09-05
> **Mark Phelps said:**
> Yeah -- such questions related to Alpha/beta versions of Ubuntu belong in the appropriate Development forum, not here.
Woops. Sorry about that! Haven't posted questions about Ubuntu Pre-releases here before, didn't realise there was an area specifically devoted to that... although, that does make a lot of sense come to think of it. *slaps head*

> **VMC said:**
> Please read the stickies, specifically this [one]("http://ubuntuforums.org/showthread.php?t=1479146") regarding partial upgrades.
Thanks for that, made for good reading. I have done this before, back with the 8.04 alphas, but it's good to know more about this sort of stuff. :)


> **ranch hand said:**
> 
Do not rush.  Think it through.
It is, at this point, not too late to come to your senses and wait a few weeks for the RC or Final.
I probably should have mentioned I was doing this on a secondary testing machine, not on my primary computer, but thanks for your concern (and help) regardless :D

---

