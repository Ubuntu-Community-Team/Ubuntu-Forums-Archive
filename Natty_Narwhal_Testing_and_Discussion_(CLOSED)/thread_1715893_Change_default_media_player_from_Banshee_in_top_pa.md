---
title: "Change default media player from Banshee in top panel"
date: 2011-03-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Mesanna on 2011-03-27
The volume icon on the top panel integrates with Banshee, however my favourite media player is Exaile. Is there any way to make the controls work with Exaile instead of Banshee when clicking the volume icon?

I've changed all the settings I can see to make Exaile my default media player, i.e. I've chosen Exaile in Preferred Applications, and have set MP3, FLAC  & OGG all to open with Exaile, and I've restarted to see if that made a difference, but Banshee still shows on the Volume icon.

Is this something the Exaile developers would need to work on, or is there a setting somewhere I can change myself?

Thanks!

---

### Post by mc4man on 2011-03-27
> Is this something the Exaile developers would need to work on, or is there a setting somewhere I can change myself?
The former

Edit: IF running unity and desired you could add Exaile to the systray whitelist and test if it caused any issues (it adds and works fine, you'd be looking to see if it caused issue else wise

Re-edit: a little testing suggests that having in the systray is ok, but, at least here, exaile does seem to cause some minor issues with the launcher at times (not related to whether systray is enabled, more if one adds, then minimizes exaile to launcher

It's actually may be better in the systray, as in - don't add exaile to launcher, start exaile otherwise, then quit from launcher, will stay active in systray and doesn't mess w/ the launcher

Don't particularly use exaile so probably won't look further till closer to release, things change

---

### Post by rburkartjo on 2011-03-27
yes mac exaile is the best far better than banshee.the cats meow imho

---

### Post by rburkartjo on 2011-03-27
and i havent been able to get exaile to work until the last updates.

---

### Post by rburkartjo on 2011-03-27
yea i tried to remove banchee from the command line and software center dont believe it can be removed at this point but remember this is only a3. see what happens as unity progresses

---

### Post by anders_c_ on 2011-03-27
Showing up in the sound indicator has nothing to do with being the default app, you can have several music players there at the same time. You would need a plugin to be able to control it from there.

Edit: I think this is what you are looking for:
[https://bugs.launchpad.net/exaile/+bug/618483]("https://bugs.launchpad.net/exaile/+bug/618483")
[https://bugs.launchpad.net/exaile/+bug/588858]("https://bugs.launchpad.net/exaile/+bug/588858")

---

### Post by mc4man on 2011-03-28
> **anders_c_ said:**
> Showing up in the sound indicator has nothing to do with being the default app, you can have several music players there at the same time. You would need a plugin to be able to control it from there.

Edit: I think this is what you are looking for:
[https://bugs.launchpad.net/exaile/+bug/618483]("https://bugs.launchpad.net/exaile/+bug/618483")
[https://bugs.launchpad.net/exaile/+bug/588858]("https://bugs.launchpad.net/exaile/+bug/588858")
I'd keep an eye on earlier bug, did try a current plugin on github - works in 10.10, (screen), not at all in 11.04

---

### Post by Mesanna on 2011-03-28
Thanks for the replies folks. I'd hoped I'd just have to change a line of text in a configuration file somewhere and that would be it. :D

I'll keep an eye on the bugs and Exaile development and hopefully something will develop in the near future.

---

### Post by wmeler on 2011-04-10
Hoping this helps someone out there.  There are a number of related bugs here.  I've put links under the following post:

[http://www.linuxquestions.org/questions/linux-software-2/exaile-suddenly-not-working-873425/](http://www.linuxquestions.org/questions/linux-software-2/exaile-suddenly-not-working-873425/)

---

