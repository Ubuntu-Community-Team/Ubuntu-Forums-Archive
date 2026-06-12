---
title: "rdesktop, Unity and Window Borders"
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by inkFTW on 2011-04-14
I normally run a few rdesktop sessions like the one below and am running into an issue with Unity.

rdesktop -T <server> -g 1152x864 -x l -z -N -r disk:local=/home/<user> -r sound:local -0 <server>

When it connects there is no border for the window, so I can't move it.  It just sticks itself at the top left of the screen.  This is the same behavior as using tsclient and choosing to Hide Window Manager Decorations.  I'm not telling it to hide the decorations (-D) and it works fine in Classic Desktop.  The only thing I can think is that it has something to do with the global menu.  Has anyone else ran into this and/or have an idea on how to get around it?

Thanks In Advance.

---

### Post by inkFTW on 2011-04-26
After some searching and testing it looks like the problem is with the geometry parameter.  -g 800x600 and 1024x768 both work.  I'm guessing it's when I hit that 75% threshold that causes windows in Unity to auto maximize is when it's getting rid of the window borders.

---

