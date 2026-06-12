---
title: "Banshee + ipod"
date: 2010-01-18
forum: Multimedia Software
---

### Post by thockin on 2010-01-18
Banshee seems to have fixed the ipod detection problems (yay), so I'm exploring it more.

Question for banshee devs or experts:

My music library is much bigger than my ipod.  Is there a way to tell Banshee to only sync some songs (not all) to the ipod?

Tim

---

### Post by boombox1387 on 2010-01-21
Yes! if you use Banshee from the latest development version you can choose to only sync to a certain playlist.  You can get the latest version by adding the [Banshee Daily Builds PPA]("https://launchpad.net/~banshee-team/+archive/banshee-daily") to your software sources.

If "daily builds" are a little too bleeding edge for you, you can wait a week or so for another Beta release (1.5.3 - should be released on the 27th).

The interface looks more or less like this: [http://banshee-project.org/~gburt/tmp/banshee-dap-sync.png]("http://banshee-project.org/~gburt/tmp/banshee-dap-sync.png")

---

### Post by hachel on 2010-01-25
i have the daily builds and mine doesn't look like that!

---

### Post by boombox1387 on 2010-01-25
> **hachel said:**
> i have the daily builds and mine doesn't look like that!

Hmm, that's strange.  Are you sure you're up to date?  The latest daily build was added about an hour ago (I think), but the new device syncing interface has been in Banshee for a couple weeks now as far as I can remember.  If you check in synaptic, what version of Banshee does it say that you are using?  It should be something like: 1.5.3+git20100125  (I'm not 100% sure about all of this; I build banshee from git master, so mine might be a little different, but I'm positive I didn't do anything special to get this device interface.  If you're using an iPod with a version of Banshee from the past couple weeks, I think the screen should look like this...)

Is your iPod syncing correctly otherwise? just using the old interface?

---

### Post by hachel on 2010-01-25
synaptic says mine is called 1.5.4~really1.5.2-0ubuntu1~hyper2~karmic

when I right-click and hit properties, and then the "versions"-tab I can see the 1.5.3~git-version.
But it doesn't show under update-manager.

So apparently I have a version with a higher version-number, but which is actually older.

so which one should i install?=

PS: i can force-install the git-version

PS2: i can sync fine with my current version

---

### Post by boombox1387 on 2010-01-25
> **hachel said:**
> synaptic says mine is called 1.5.4~really1.5.2-0ubuntu1~hyper2~karmic

when I right-click and hit properties, and then the "versions"-tab I can see the 1.5.3~git-version.
But it doesn't show under update-manager.

So apparently I have a version with a higher version-number, but which is actually older.

PS: i can force-install the git-version

PS2: i can sync fine with my current version

It all makes sense now.  An accident happened with the Stable PPA a few weeks ago.  The Banshee 1.5.3 daily build was accidentally uploaded to the Stable PPA instead of the Daily PPA.  The version on the Stable PPA was supposed to be 1.5.2, but Launchpad doesn't allow package maintainers to upload a version that is older than the current version.  The only way to prevent people using the Stable PPA from updating to a daily build was to re-version 1.5.2 to 1.5.4. (confusing, huh?)

Since you're using both the Stable and the Daily PPAs, your package manager thinks you're using 1.5.4, when really you're using 1.5.2.  As long as you have Banshee installed from the Stable PPA, your package manager won't let you update to 1.5.3, because it really thinks you would be downgrading from 1.5.4.

If you really want to use the daily builds, I would remove the Stable PPA from your software sources, and either uninstall Banshee and reinstall, or force-install the git version.  Either way, you might want to make sure your ~/.config/banshee-1/banshee.db is backed up before you do too much.

---

### Post by hachel on 2010-01-25
ok, cool

thanks for the info

---

