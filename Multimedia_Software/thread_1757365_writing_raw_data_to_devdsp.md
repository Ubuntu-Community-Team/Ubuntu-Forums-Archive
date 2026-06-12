---
title: "writing raw data to /dev/dsp"
date: 2011-05-13
forum: Multimedia Software
---

### Post by LanguidLegend on 2011-05-13
I'm having trouble with a little exercise in my CS class:
[INDENT][COLOR="DimGray"]_Redirecting mouse device into a file_

sudo cat /dev/input/mice > rawmouse.data
Move the mouse a bit and then type CONTROL-C.

[I]Note that on some distro's you'll need to sudo to bypass device files' restricted permissions.
[/I]
Now, cat that file to the sound card.

cat rawmouse.data > /dev/dsp

Sounds horrible, doesn't it?
So that's how we make sound, by throwing bytes at the sound card.[/COLOR][/INDENT]
Here's my issue: I follow those directions, but it remains silent.. Any ideas why?

_Note:_ I am running Ubuntu 10.10, and my sound is at max volume.

---

