---
title: "Updated from 10.10 to 11.04 A3, weird window behavior"
date: 2011-03-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by blm14 on 2011-03-21
So I upgraded to 11.04 basically to see if it would fix my touchpad problem (I have a dell N5030 which uses an ALPS touchpad and I cannot disable tap-to-click, a whole OTHER discussion)...

I don't want to use Unity, because I like compiz and especially I like desktop cube.

So I am using the "ubuntu classic desktop" option when I log into X. I am seeing several problems:

1) Screenshots not working (!!!) I checked in keyboard settings and screenshot is set as <print> and screenshot of a window is set to <ALT PRINT> and neither one is working. I wanted to use it to show what my OTHER problems are below but no dice :(

2) My top nav bars are missing. This is the bar at the top which would ordinarily show the minimize, close and maximize buttons as well as provide a place for me to move a window around the screen. Very annoying.

3) I have enabled OpenGL, desktop cube and rotate cube in Compiz Settings Manager. It appears that I have a 2x2 set of workspaces but when I do desktop cube it appears as a flat surface with only one workspace.

HELP!

---

### Post by blm14 on 2011-03-21
Hrm well I at least figured out how to get desktop cube working-ish as I want (1x4 instead of 2x2)... But I still have no top bar and new windows open up such that the top of the window bleeds into the gnome bar. Like as if the top of each window is sitting under "Applications Places System"

I would take a screenshot but I can't seem to do that either ARGH

---

### Post by uRock on 2011-03-21
Moved this to NNT&D

---

### Post by blm14 on 2011-03-21
playing, playing, getting closer.

I got screenshots working, so this is what I am seeing:

[img]http://img708.imageshack.us/img708/341/screenshotcomaiba.png[/img]

See there's no bar at the top there with the close/minimize/maximize buttons. 

And new windows still spawn kind of under the gnome panel at the top of the screen.

---

### Post by blm14 on 2011-03-21
alt-tab not working, <super>-w for window picker also not working.

What gives!?

---

### Post by uRock on 2011-03-21
> **blm14 said:**
> alt-tab not working, <super>-w for window picker also not working.

What gives!?
Did you not realize this is the developmental version?

---

### Post by VMC on 2011-03-21
> **blm14 said:**
> playing, playing, getting closer.

I got screenshots working, so this is what I am seeing:

[img]http://img708.imageshack.us/img708/341/screenshotcomaiba.png[/img]

See there's no bar at the top there with the close/minimize/maximize buttons. 

And new windows still spawn kind of under the gnome panel at the top of the screen.

> You also need a window decorator, which is responsible for drawing the window titlebar/frame Try from a terminal  ```
compiz --replace
```, wait a few seconds and see if it redraws your screen with the decorator.

---

### Post by mc4man on 2011-03-21
As Vmc said, also ck in ccsm that Window Decoration plugin is enabled - it might of gotten unset

Also make sure you're updated - there were some conflicts between unity's super shortcuts and scale

I don't use Classic, but a quick login suggests - 

In Classic super+w should pull all open windows, can be done if focus is on a window or desktop
Also by default I think Shift+Alt+arrow up should pull all from a workspace (may only work if focus is on the desktop

(Also rotate and by default cube are usable in unity, just requires a small edit to the unityshell.xml and working thru totally unsetting all default plugins when changing from wall

---

### Post by kaldor on 2011-03-21
> **uRock said:**
> Did you not realize this is the developmental version?

This. You seem to think Natty is stable. It's not even a beta yet. Oh well, now that you got it installed you can help with reporting bugs :)

---

### Post by blm14 on 2011-03-22
I will report bugs. A chastised, I haz.

<sigh>

---

