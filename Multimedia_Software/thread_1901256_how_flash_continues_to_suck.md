---
title: "how flash continues to suck"
date: 2011-12-28
forum: Multimedia Software
---

### Post by esj on 2011-12-28
I've tried 3 well respected techniques of installing flash. tried 4 different video drivers for nvidia.  flash always breaks.  most common is that something goes wrong and x.org hits 95-100% cpu usage and everything is frozen out.  instability increases with dual screens

I've seen this kind of behaviour in other apps.  something goes wrong and x.org consumes all available cpu.

any ideas?

fwiw, flash is my only "must-have" tool for facebook and hulu.

now dual screen have their own problems.  you can't arrange the relationship so the screens are 
2
1

instead of being stuck as:
1 2

---

### Post by Paddy Landau on 2011-12-28
Interesting; I have had no problems with Flash except for a brief period earlier this year when Adobe messed up 64-bit Flash. You'll be pleased to know that Flash is being phased out in favour of HTML 5.

Have you tried the add-on [Flash Aid]("http://www.webgapps.org/add-ons/flash-aid"), also [available from Mozilla]("https://addons.mozilla.org/firefox/addon/flash-aid/")?

---

### Post by esj on 2011-12-28
> **Paddy Landau said:**
> Interesting; I have had no problems with Flash except for a brief period earlier this year when Adobe messed up 64-bit Flash. You'll be pleased to know that Flash is being phased out in favour of HTML 5.

Have you tried the add-on [Flash Aid]("http://www.webgapps.org/add-ons/flash-aid"), also [available from Mozilla]("https://addons.mozilla.org/firefox/addon/flash-aid/")?

yes, I've used flash aid and it only made things worse.

I've been following the development of html 5 for a while.  I've built a web development framework for hand disabled, speech recognition using people like myself and I hope I can update it to html 5 rsn.

as nice as html 5 is, it does me no good because hulu only uses streaming flash.  as for facebook, well, my girlfriend uses it, er,ah, yeah.  

I did some more testing this am.  the greyout/screen lock happens when the X server goes to 100%  I see it with thunderbird, any browser, emacs, and most frequently flash.  the problem is worse when I'm using dual monitors.  am I looking at an X server bug?

---

### Post by Paddy Landau on 2011-12-28
Yes, it will be quite a while before HTML 5 completely replaces Flash.

As it is not only Flash but also other programs, it sounds as though your video driver doesn't easily handle the resolution required for your set-up.

Try the following to test:

[LIST]
[*]Use just one monitor. Do you notice any difference?
[*]Turn off effects (log out and log back in to Classic mode with "no effects"). Does that make a difference?
[*]Still in Classic mode, go back to using two monitors. Any difference?
[/LIST]
That should, I hope, help to narrow down the problem.

---

### Post by esj on 2011-12-28
> **Paddy Landau said:**
> Yes, it will be quite a while before HTML 5 completely replaces Flash.

As it is not only Flash but also other programs, it sounds as though your video driver doesn't easily handle the resolution required for your set-up.

Try the following to test:

[LIST]
[*] 1) Use just one monitor. Do you notice any difference?
[*] 2) Turn off effects (log out and log back in to Classic mode with "no effects"). Does that make a difference?
[*]  3) Still in Classic mode, go back to using two monitors. Any difference?
[/LIST]
That should, I hope, help to narrow down the problem.

1) yes, one monitor is marginally better.  I only need to power cycle 2-3x day vrs 5+
2) thought I had but I will check.

3) brb, checking :-)  

thanks for the help.

* update *
2d seems seems to help in the first 5 min. oddly, hulu will not stay in full screen mode.  I will update later today on how often flash triggers this crash.

I think you are right about the driver.  that could cause the X11 server to go out to lunch.  is the oss nvidia driver good enough to use in production?  screen 0  is 1920x1200, screen 1 is 1440x900.  I'm also frustrated that it insists on being  side by side and not top and bottom

---

