---
title: "Page down/page up no longer work in .22?"
date: 2010-03-27
forum: Mythbuntu
---

### Post by dsbw on 2010-03-27
So, I upgraded my mythtv a few weeks ago and after some initial mistakes, got everything running.

But! We have about 2000 recorded shows. And we rely pretty heavily as a result on being able to page through the "Watch recordings" list. (#3 and #9 on the remote.)

But the page up/page down doesn't seem to work any more! I thought maybe it was a theme issue, but I have no page up/page down on any theme.

If I go into the keys setup, though, it shows #3 and #9 attached to page up/page down. :x

Thoughts?

---

### Post by dsbw on 2010-04-10
No ideas, anyone?

---

### Post by tgm4883 on 2010-04-10
Are you using a keyboard? I got to think maybe your remote keys aren't binded to pgup/pgdown anymore.

---

### Post by dsbw on 2010-04-11
Nope. Just a plain old MCE remote. 

I think I see what happened: Previously '3' and '9' weren't used and were interpreted as pageup and pagedown, like they would be on a numpad. Now, apparently, they're used globally for their respective numbers.

My attempts to override failed for some reason. (It asks you if you want to conflict with the global settings, even if you're in the global settings, and then ignores you if you say you do, apparently.)

But I found a couple of buttons ("r" and "s") which weren't being used and put those in. Problem solved, after a fashion.

---

