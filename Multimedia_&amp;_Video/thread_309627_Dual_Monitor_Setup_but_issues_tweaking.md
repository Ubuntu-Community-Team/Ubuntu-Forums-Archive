---
title: "Dual Monitor Setup but issues tweaking"
date: 2006-11-29
forum: Multimedia &amp; Video
---

### Post by tannedin on 2006-11-29
I'm trying to get my set up perfect, and I'm about half way there; however there are some issues.

Setup is currently Edgy on a IBM Z60m (Radeon Mobility X600) using the restricted ati drivers.  Display0 is the laptop screen (1280X800) and Display1 is an Acer AL1916W LCD connected to the laptop via the video out.

I tried using the aticonfig, and I want two different screens not one big screen.  The 'default' multiscreening via "System Settings" allows me to maximize windows in either the primary or secondary display while still keeping multiple desktops, something that running aticonfig with numerous options and attempts did not.

The 'perfect scenerio' would fix the following errors:
1.) Font DPI (I think) is off in the primary display.  KDE programs are served correctly, however in Firefox the fonts are larger.  Attempting to fix this with "force Font DPI" via System Settings -> Appearence -> Fonts however, that didn't do anything.

2.) Display1 is set up so it is left of Display0, however when I mouse over to that screen my mouse turns into a pixilated cube.  I found somewhere on the boards a xorg.conf fix by adding
```
Section "Extensions"
  option "Composite" "disable"
EndSection
```
However, that did not fix the issue.

3.) I have to set the resolution on Display1 to 1600x1200 to prevent a "screen roll".  Basically, the entire screen will not display all at once and mousing the boundaries (which the computer identifies) scrolls through the screen.
-----
On a side note, cloning the current desktop works wonderfully, but not what I'm looking for


Any ideas?

---

