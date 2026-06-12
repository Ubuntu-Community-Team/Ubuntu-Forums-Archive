---
title: "How to prevent Light-Locker from disabling VSYNC?"
date: 2014-08-31
forum: Multimedia Software
---

### Post by fidelis2 on 2014-08-31
A kind person recently suggested here in the forum, that in order to enable Vsync in Xubuntu (or was it Ubuntu?), so that your moving graphics, video etc. doesn't tear anymore, you can do this:
open in the configuration center the "window fine tune tool" (freely translated from my localised version to English), enter its tab "Compositor" and there enable the option "Synchronize drawing to vertical blank".

This works very fine. (OK, so there's still some tearing in the upper-most part of the screen, but with letter box applications this isn't visible.)

Now I noticed however that whenever the Light Locker comes into effect and the screen goes black, and then I press some key to see the desktop again, the "wait for the vsync" effect is gone and the tearing is there again. The mentioned option in the "compositor" tab is still enabled however, just it's not working anymore.

So far I only found two solutions which aren't very handy however:
1) Re-boot the system, so that the setting is being used again.
2) In the configuration center, deactivate the entire compositor (there's an radio button box in the mentioned tab), and enable it again. The screen flickers for a second and everything works again.

Does anybody know a nicer solution? (Like how to tell Light Locker not to disable the Vsync setting?)

---

