---
title: "App menu not working"
date: 2011-01-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by fluteflute on 2011-01-09
I believe I have all the relevant packages installed, but all I get in my Application Menu is File->Close

What could be wrong?

---

### Post by fluteflute on 2011-01-16
I don't like to bump but this problem is persisting - I'd prefer not to have to reinstall (though I guess it is only a Virtual Machine... :P)

---

### Post by castrojo on 2011-01-16
Have you done all the updates? The menus were acting weird all last week but should be fixed by now.

---

### Post by fluteflute on 2011-01-17
> **castrojo said:**
> Have you done all the updates? The menus were acting weird all last week but should be fixed by now.
Yes I have, thanks for the suggestion though Jorge.

---

### Post by cariboo on 2011-01-17
I've been having a problem when a terminal is open, the menu works the first time I click on it, but nothing afterwards. This is only happening on my main system at home, my netbook is OK.

---

### Post by fluteflute on 2011-01-17
Tried removing the indicator-application package and restarting - it made absolutely no difference. (Reinstalling it again didn't change things either.)

---

### Post by efflandt on 2011-01-17
I have never seen a File > Close menu at the top when Firefox is full screen.  As of updates I last did Saturday full screen Firefox window controls and window title end up in the panel, and if I move mouse to top panel the title just disappears (no menu there).  At that time I updated using Synaptic, Custom Filters > Upgradable (upstream) and Mark All Upgrades (USA).  That worked fine at that time and I have not yet done updates since then.  Note that some repos are up to a week behind current.

I did have an issue with Terminal menu in top panel becoming grayed out (black text on dark gray background) and unresponsive.  But that was while experimenting with a script a poster was having trouble with (which at some point made my prompt go inverse), but otherwise the Terminal menus work fine.

PS: Since further updates I do initially see that "File" in top panel before opening anything else, but with nothing open there is no menu for it.  And right click does not work for anything until after right clicking on desktop.

---

### Post by jennybrew on 2011-01-17
Yes Im seeing that as well after Firefox has been running.
Just click on Ubuntu logo ..the app menu ..shut the resultant window down and everything will be fine again.

---

### Post by chrisccoulson on 2011-01-17
> **cariboo907 said:**
> I've been having a problem when a terminal is open, the menu works the first time I click on it, but nothing afterwards. This is only happening on my main system at home, my netbook is OK.

I've been debugging a couple of bugs that are breaking the appmenu at the moment ([bug 703769]("http://launchpad.net/bugs/703769") and [bug 703689]("http://launchpad.net/bugs/703689"). Perhaps your issues are related to those.

---

### Post by cariboo on 2011-01-17
> **chrisccoulson said:**
> I've been debugging a couple of bugs that are breaking the appmenu at the moment ([bug 703769]("http://launchpad.net/bugs/703769") and [bug 703689]("http://launchpad.net/bugs/703689"). Perhaps your issues are related to those.

Thanks I subscribed to both.

---

