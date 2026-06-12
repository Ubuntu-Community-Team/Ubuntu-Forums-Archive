---
title: "Gmail messes up display resolution"
date: 2010-05-04
forum: Multimedia Software
---

### Post by smbell on 2010-05-04
So this is a really strange problem.  Fresh install of lucid i386. Nvidia 6800 Ultra card.

Symptoms:
When I go to gmail within a few seconds the screen goes blank (black) as if it's changing resolution.  It may do this a few times. After one or more times the screen will stop flashing, but it will be stretched diagonally with the top corners in the right spot, but the bottom of the screen is shifted and wrapped to the right by about a third of the screen size.  If I'm using the nvidia drivers I can open up the nvidia tool (although its a bit hard to see) and change the resolution to something else and back to fix it.

Things I've tried:

[LIST]
[*]Nvidia driver (current recommended)
[*]Nvidia driver 173
[*]remove nvidia driver and use default driver
[*]Uncheck Sync to VBlank in Nvidia tool
[*]Used both firefox and chrome browser
[*]deleted xorg.conf
[/LIST]
Only gmail seems to trigger the problem.

---

### Post by smbell on 2010-05-04
Update:
Was able to recreate the problem with thunderbird.  But it only seemed to happen on a particular account (thunderbird is only connected to a couple of comcast mail accounts).

---

