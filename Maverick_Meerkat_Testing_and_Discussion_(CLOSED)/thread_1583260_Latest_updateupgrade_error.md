---
title: "Latest update/upgrade error"
date: 2010-09-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Quackers on 2010-09-27
I've had the python-virtkey error for the last couple of updates but read the thread here and decided to wait for further developments. On running Update Manager a few minutes ago I had updates to run. On running them it turned into an upgrade and on running that it said some things could not be installed and that I should run a partial upgrade. Having run the partial upgrade it just keeps coming back with the same message (see screenshot).
Do I need to be concerned? Or do something? Thanks

---

### Post by cariboo on 2010-09-27
See [this]("http://ubuntuforums.org/showthread.php?t=1582716") thread.

---

### Post by Quackers on 2010-09-27
I don't understand what a thread discussing "ubuntu-extras-keyring" has to do with my question. Unfortunately.

---

### Post by superhick on 2010-09-27
see: [http://ubuntuforums.org/showthread.php?t=1479146](http://ubuntuforums.org/showthread.php?t=1479146)

---

### Post by Quackers on 2010-09-27
Yep, seen it. So I'm running an update, which becomes a partial upgrade. This comes after the python-virtkey error for which there is a thread where the last post states that the problem is fixed via the latest updates. That's partly the reason I'm running the update. To fix the python-virtkey error.
Now, call me naive, but I thought that maybe the partial upgrade would run (fixing the python-virtkey error) and then the rest of the upgrade would run. As I say, naive, maybe, but not out unreasonable.
So,what I should have done is question the partial upgrade? Have a look at which packages were to be installed/deleted (like that would mean anything to me! :-))
and then what? Not do it? Leaving the supposedly fixable python-virtkey error as it was. 
Ok, I'll know for next time.

---

### Post by cariboo on 2010-09-27
Usually when you are presented with a partial upgrade, or one that wants to remove important packages, it is up to you whether you want to do the upgrade of not. 

When running a testing version, it is suggested you use either synaptic of the terminal.

I just went to do an upgrade, and it wanted to remove gnome-terminal, so instead of using synaptic, I opened a terminal and typed:

```
sudo aptitude safe-upgrade
```

which did the upgrade without removing anything, there are still two packages in the queue, but I sure an update later on today, or tommorow will solve the problem.

BTW aptitude is no longer installed by default, so it needs to be installed before using.

**Edit:** there is also a sticky at the top of the page about partial upgrades.

---

### Post by Quackers on 2010-09-27
Thanks for your time cariboo907.
I have run updates previously that deleted packages and had no problem. Knowing that there are other options, such as sudo aptitude safe-upgrade, would be helpful but sadly, I don't have much experience.
So, am I correct in thinking that you don't use Update Manager at all? That would seem to suggest that its existence is a waste. 
Hmm I have much to learn.
I intend to re-install Meerkat when its final version appears so I'm only messing with it at the moment. Seeing what's new etc. As long as it boots I'm happy :-)
If future partial upgrades appear I'll ignore them and give it 24 hours before I look again.

---

### Post by cariboo on 2010-09-27
Once a release is final, using update manager is the preferred way to update, during testing because there are so many changes daily, it is safer to use synaptic package manager or update from a terminal. even today, the updates are coming fast and furious.

The RC is supposed to be released on Thursday, so things should slow down a bit, and it would probably be safe to use the update-manager again.

---

### Post by Quackers on 2010-09-27
Ok, thanks for the info Mr.Cariboo :-)

---

### Post by ronacc on 2010-09-27
one word of caution , even after release be very careful if update manager offers a  partial upgrade , they are dangerous at any time , if you aren't sure they won't remove something vital it is better to wait or do as cariboo has suggested .

---

### Post by Quackers on 2010-09-27
I'll do that, ronacc, thanks. Looking at your avatar I thought there was a second caribooooo :-)

---

### Post by M4570D0N on 2010-09-27
Some update issues just came up in synaptic:

libgtk2.0-bin and libgtk2.0-common updates are showing up to upgrade from 2.21.7-1ubuntu1 to 2.22.0-0ubuntu1, however they cannot be updated because it depends upon libgtk2.0-0 2.22.0-0ubuntu1 but there is no update for it from 2.21.7.


Synaptic wants to upgrade to a new version of  evolution-data-server-common (2.30.3-2ubuntu1) but wants to remove evolution-data-server

Synaptic wants to upgrade to a new version of libgnome2-common (2.32.0-0ubuntu1) but wants to remove:

aptoncd
bleachit
deskbar-applet
gdm
gdm-guest-session
giver
gnome-about
gnome-about
gnome-applets
gnome-dictionary
gnome-mag
gnome-panel
gnome-power-manager
gnome-utils
gufw
indicator-applet
indicator-applet-session
libbonoboui2-0
libgail-gnome-module
libgnome2-0
libgnome2-pearl
libgnome2.24-cil
libgnomepanel2.24-cil
libgnomeui-0
liblpint-bonobo0
libpanel-applet2-0
mintmenu
mousetweaks
nautilus-share
python-gnome2
python-gnome2-desktop
sensors-applet
screenlets
tomboy
startupmanager


and probably a dozen or so more, but you get the idea. This can't possibly be correct, can it?

---

### Post by ktp on 2010-09-27
just be patient...packages are most likely getting upgraded to get ready for RC and it might be taking little while for all the dependencies being updated/loaded to repository.  As others have said this is not uncommon during development release and thus there is sticky thread dedicated to it.

---

### Post by mc4man on 2010-09-27
> When running a testing version, it is suggested you use either synaptic of the terminal.

This keeps getting repeated and is absolutely untrue. There is no reason not to use the update manager as the primary means for updates/upgrades and use synaptic (or cli ) when needed to complete updates or see why they can't be done atm.

I've never used the cli thru numerous dev's and never had an issue due to the manner of updating.

It's quite simple - never accept a pop up from update manager offering a partial, you can always allow update manager to install what it's able to normally.
If packages are greyed out then use synaptic to see why, many times it's able to complete the action successfully/safely or will provide clues as to why not

The biggest advantage of update manager is that all the package info is right there in plain sight including the changelogs or links to changelogs.
(unless reading such things is considered not advisable prior to install?
Other smaller are you can pick and choose not to do all at once, and it shows them all  - at times synaptic will not list all.

---

### Post by Quackers on 2010-09-27
Thanks for all the info people. Very useful to know.

---

### Post by jdorenbush on 2010-09-28
Unfortunately I made the mistake of running the "partial upgrade". Doh!

Any suggestions for how to get out of this mess?

---

### Post by Lucretius on 2010-09-28
I ran it by accident and it removed:

evince 
furiusisomount 
nautilus-share 
totem 
totem-mozilla 
totem-plugins
ubuntu-desktop

wait until the dependency issues are resolved and update your system.

then re-install the packages

at no time should you reboot

---

### Post by Quackers on 2010-09-28
I had 6 packages that were greyed out in Update Manager. The latest round of updates, just completed, seems to have fixed all problems.
My life can continue now :-)

---

### Post by 23meg on 2010-09-28
> **mc4man said:**
> The biggest advantage of update manager is that all the package info is right there in plain sight including the changelogs or links to changelogs.
(unless reading such things is considered not advisable prior to install

Why would it be? By reading changelogs, you know what changes to look for, what to test, what might have been the cause of a recent breakage you've had and so on. One would wish more people read changelogs, and more often.

Another advantage is that you actually get to test Update Manager itself.

---

### Post by jdorenbush on 2010-09-28
> **Quackers said:**
> I had 6 packages that were greyed out in Update Manager. The latest round of updates, just completed, seems to have fixed all problems.
My life can continue now :-)

Yep, same here. That was an annoying couple of hours, hah. Glad it's fixed though. =D>

However, I had to switch to the "Main Server" in my Software Sources because the mirror I was using wasn't picking up the upgrades for some reason. So if anyone else is dying to get these upgrades and aren't seeing them, try switching your server.

---

