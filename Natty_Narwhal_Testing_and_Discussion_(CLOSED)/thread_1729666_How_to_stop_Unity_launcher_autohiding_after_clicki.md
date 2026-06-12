---
title: "How to stop Unity launcher autohiding after clicking on an icon?"
date: 2011-04-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by SevenMachines on 2011-04-15
When i flick the mouse to the left screen edge, the unity launcher pop out. When i click on the icon to switch application or start one, the launcher autohides. I'd prefer it stayed open until i moved the mouse off of the launcher, is there any way to do this?

---

### Post by r-senior on 2011-04-15
Have you tried the different settings for launcher hiding?

Compiz Config Settings Manager -> Unity Plugin

They don't sound like exactly what you suggest but "dodge active window" might be an improvement?

---

### Post by SevenMachines on 2011-04-15
It cant be done with compiz settings or gconf, so it seems anyway, just wondering if anyone had some special sauce for it. or a little patch or something.

---

### Post by wojox on 2011-04-15
Hide Launcher > Never works here.

---

### Post by mc4man on 2011-04-15
With hide mode 1 (autohide) they set a 1 sec timeout (barely), to move the cursor in the launcher area after clicking on an icon. If you do that the launcher will stay exposed as long as cursor is in launcher area

This doesn't account for windows that produce pop ups that require your attention (ex. synaptic with password auth window, 
Semi requested that 'mouse over launcher' be maintained once established, didn't fly.
May be adjustable in the source, would take some digging though there is always the super button

(here have created a toggle switch to go between mode 0 and mode 1 which sorta helps, usually use autohide, at times just want it exposed

Edit: they've also since introduced 'edge reveal' so as window from icon click is opening you can just move cursor to left edge to re-expose launcher

---

### Post by SevenMachines on 2011-04-15
Yep, the timeout does seem a little quick, or my thought process is a little slow :) particularly noticing it when flicking between open windows comparing things, the launcher is closing enough times for it to be a bit annoying. Looks like maybe LauncherHideMachine.cpp could be where to fiddle with it to not autohide but theres plenty of updates, maybe when its stable i suppose. Hopefully when unity's stabilised a bit itll be worth adding some sort of configuration tools to it. yes, 'edge reveal' makes it a bit more natural, at least to me.

---

### Post by frncz on 2011-04-15
You have to install ccsm using synaptic or the ubuntu software center
This stands for compiz configuration setting manager, I think
If you then run ccsm in a terminal, you will have lots of choices (not enough) to modify the system.
Look for the Unity option. In there, you can click on 'never' to change the behaviour of the icons.

---

### Post by SevenMachines on 2011-04-15
> **frncz said:**
> You have to install ccsm using synaptic or the ubuntu software center
This stands for compiz configuration setting manager, I think
If you then run ccsm in a terminal, you will have lots of choices (not enough) to modify the system.
Look for the Unity option. In there, you can click on 'never' to change the behaviour of the icons.
Yes, i'm aware of the available options from ccsm and laterally through gconf. Its not a question of never autohiding sadly, its an adaptation of the autohide behaviour i was looking for. i think mc4man's right, i would need to fiddle the behaviour in the source, its probably not a big enough deal for me to bother doing it though, apart from for funsies :)

---

### Post by SevenMachines on 2011-04-15
Well, i've set the autohide delay to 2 secs instead of 0.75secs but if anyone works out a way to keep it open after clicking an icon without moving the mouse let me know

---

### Post by mc4man on 2011-04-15
I may file another bug (more likely for 11.10), based on that while the 1 sec may seem fine in theory, in practice it's not.
You almost have to do a click and move as one action, while at least here my attention is always on the icon clicked,  seeing if it reacts, by that time it's too late
(in any event it'll be considered of very low importance

---

### Post by SevenMachines on 2011-04-15
Yeah, probably best for 11.10 but i doubt itll see much movement as a default, maybe being able to user configure things like that will though.

---

### Post by mc4man on 2011-04-15
> **SevenMachines said:**
> Well, i've set the autohide delay to 2 secs instead of 0.75secs but if anyone works out a way to keep it open after clicking an icon without moving the mouse let me know
Do tell...

Edit: nv - obvious

---

### Post by Xgen on 2011-04-15
The only way I can get it to do what the OP wants is to keep the mouse against the side of the screen when I click on the launcher icon. The launcher remains open when the program starts, and then I can slide up/down to other launcher icons.

---

### Post by SevenMachines on 2011-04-15
the delay_timeout is in LauncherHideMachine.cpp in the constructor. On a quick look you could probably tailor the autohide behaviour criteria in LauncherHideMachine::EnsureHideState using 'quirks', maybe testing fiddling with MOUSE_OVER_LAUNCHER tests. Not much point while updates are coming so often though, better would be a configuration mechanism rather than recompiling, i dont know what/if there are plans for that though

---

### Post by mc4man on 2011-04-15
I guess i need a fresh install or something else? - oddest thing, have never had issue building unity, been doing ever since 'true-hide' was turned into 'intelli-hide'

Anyway get this (red mine
> dpkg-source: info: building unity in unity_3.8.8-0ubuntu2+nmu1.dsc
 debian/rules build
dh build --with translations --with quilt
   dh_testdir
   dh_quilt_patch
	quilt --quiltrc /dev/null push -a || test $? = 2
[COLOR="Red"]Applying patch 001_static-linking-dont-query-immodules.patch[/COLOR]
patching file configure.in
Hunk #1 FAILED at 150.
1 out of 1 hunk FAILED -- rejects in file configure.in
patching file modules/input/Makefile.am
Hunk #1 FAILED at 176.
Hunk #2 FAILED at 238.
2 out of 2 hunks FAILED -- rejects in file modules/input/Makefile.am

can't see where this is coming from
So if I create a /debian/patches dir, put in a series file listing that patch and comment it out then the build goes fine - weird

---

### Post by SevenMachines on 2011-04-15
hmm, strange. i was using a cmake local build but it debuilds fine too. no +nmu1 version though, i'm taking it thats yours/a ppas build.

---

### Post by mc4man on 2011-04-15
> **SevenMachines said:**
> hmm, strange. i was using a cmake local build but it debuilds fine too. no +nmu1 version though, i'm taking it thats yours/a ppas build.

Just sometimes use a new changelog entry w/ a +nmu1 so packages don't inadvertently get upgraded until there is an actual upgrade available

Did figure it out (sorta of, but not really), I'd pulled a debian folder from something else that had that patch in it. The debian folder was just sitting on the Desktop, the unity source was in a separate folder on the Desktop. It was, as seen, interfering.
never seen that before but that's nothing new..

edit: anyway the 2 sec delay works ok, doesn't seem bad from a 'design' perspective

---

