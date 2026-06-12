---
title: "Two Opera / Unity bugs"
date: 2011-04-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by PaulW2U on 2011-04-06
After yesterday's updates I noticed that the Opera launcher icon was behaving strangely. I have an Opera icon permanently on Unity's launcher. If I start Opera then another icon appears, that of the Opera Widget Manager. The small arrow that indicates an application is active shows on OWM's icon and if I minimize Opera and want to restore it then I must use the OWM icon. The main Opera icon shows no such indicator at all and although it "pulsates" when clicked it doesn't seem to perform any other function apart from starting Opera initially.

After today's updates of a couple of hours ago a second problem has occurred. If I open an Opera favourites folder from the Bookmarks menu it is displayed but doesn't disappear if I open another folder next to it on the Bookmarks menu. Each folder is displayed with some corruption at the top of the menu until I actually select a bookmark and Opera displays the new web page.

I don't know which update caused the first problem but the second may be the fault of compiz as a number of applications were behaving strangely immediately after the update and before I logged out and back in again. I'm using build 2079 of the latest Opera beta but as it's behaving normally while using the Classic desktop option I think Ubuntu is at fault. I haven't submitted any bug reports yet as I'm not sure against which application they should be logged.

Anyone experiencing any similar problems with either Opera or other programs?

Edit: I've just updated to build 2081 and the menu problem has gone but the first problem remains.

---

### Post by screaminj3sus on 2011-04-06
same problem here, very annoying. I am using the latest opera barracuda RC.

---

### Post by mc4man on 2011-04-06
I would file a bug on or wait out, maybe it will straighten itself out. (even if it does then may require a reinstall

You'll notice that if opera isn't installed, or if it is then  a purge, restart and install, that it works as expected the first time. After a log out/in it gets changed to where opera-browser.desktop opens and then once open opera-widget-manager.desktop controls it.

There is a quite improper hack around this, I guess if not fixed I'll post how.
screen shows 'fixed'

---

### Post by screaminj3sus on 2011-04-06
Enlighten me, I love improper hacks :)

---

### Post by mc4man on 2011-04-06
posted possibly  a better solution in bug report

---

### Post by screaminj3sus on 2011-04-06
thanks, I did try shortening to just the last part to see if it would work and it does :)

---

### Post by mc4man on 2011-04-07
> **screaminj3sus said:**
> thanks, I did try shortening to just the last part to see if it would work and it does :)

This laptop's install, even though it's only 5 days old, must be a bit screwed up, I had to do all of that to get it to take.
(been testing some proposed patches,  
Guess it's time for a fresh install..

---

### Post by PaulW2U on 2011-04-07
Launcher icon bug reported - [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/754019](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/754019)

---

