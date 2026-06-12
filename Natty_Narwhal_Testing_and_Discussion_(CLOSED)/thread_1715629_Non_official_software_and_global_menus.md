---
title: "Non official software and global menus"
date: 2011-03-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rajeev1204 on 2011-03-27
I tried many applications like sflphone and xqf server browser which dont have either a global menu or  a standard menu making these applications totally useless.

So unity is only for official packages? Rest have to use classic desktop?

---

### Post by r-senior on 2011-03-27
Have you tried disabling the global menu for these applications?

Edit /usr/share/applications/<application>.desktop andchange the Exec line as follows:

```
Exec=env UBUNTU_MENUPROXY=0 <application>
```

Note that subsequent upgrades may overwrite the .desktop file.

---

### Post by beew on 2011-03-27
> **r-senior said:**
> Have you tried disabling the global menu for these applications?

Edit /usr/share/applications/<application>.desktop andchange the Exec line as follows:

```
Exec=env UBUNTU_MENUPROXY=0 <application>
```Note that subsequent upgrades may overwrite the .desktop file.

Removing the global menu would leave a void in the top panel which can neither be removed nor be used for applets.

@op

Haven't thought of that. If that is the case it IS the deal breaker for me. I can put up with other things but not this. I use Matlab and Mathematica (I have Maxima and Octave as well BUT NOT AS REPLACEMENTS!)

Don't know why they push the global menu, it is such a stupid idea it is impractical to use and they make it such that it is a pain not to use it as well.

---

### Post by mc4man on 2011-03-27
> **rajeev1204 said:**
> I tried many applications like sflphone and xqf server browser which dont have either a global menu or  a standard menu making these applications totally useless.

So unity is only for official packages? Rest have to use classic desktop?
Some applications are atm unable to use the 'global menu'. This is only a real issue when, as noted, no menus are displayed at all. 
Whether they can or not most likely will come from  an upstream change.

As a user you can return the menu to the app window as posted,_you should also file a bug against the app in this regard_. At the very least the packaging can be adjusted to have menus available as installed and possibly global support added at some point if possible.

---

### Post by cariboo on 2011-03-27
I haven't looked for the email, but the devs asked that any apps that the global menu doesn't work with, should be the subject of a bug report. I'm not sure if they meant apps that aren't in the repositories, but you can always try.

---

### Post by Starks on 2011-03-27
I think Audacity was also one of these programs.

---

### Post by mc4man on 2011-03-27
> **Starks said:**
> I think Audacity was also one of these programs.
It is and by someone filing a bug on has a chance of being fixed in some manner 

[https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/731451](https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/731451)

---

### Post by teachop on 2011-03-27
> **r-senior said:**
> Have you tried disabling the global menu for these applications?
I wonder why the exception logic wasn't reversed.  Only applications that are specifically enabled, via config or some api call, to use global menus would get them.  Everything else would work normally.

---

### Post by cariboo on 2011-03-27
In Natty, normal is to use the global menu, so everything else is abnormal. :)

---

