---
title: "Firefox menus not visible?"
date: 2010-12-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by scradock on 2010-12-20
Running Natty with Unity Desktop - this morning everything opened up without any glitches (first time, AFAIR), but Firefox 4.0 Beta 7 has non-visible menus. That is, if I click on Bookmarks menu, it changes color as normal, but no drop-down list appears. BUT if I click below it I get sent to some page in my Bookmarks - very annoying not to be able to see which one in advance, of course.

And of course, Firefox menu bar is still in the browser, not on the Unity bar.

Anyone else?

---

### Post by smsmith on 2010-12-20
The menus are actually *behind* the window.  Quitting and restarting compiz fixes it for the session.

---

### Post by scradock on 2010-12-20
> **smsmith said:**
> The menus are actually *behind* the window.  Quitting and restarting compiz fixes it for the session.
Yes, I thought that must be it - the same happens from the shut-down button on the Unity bar. The options list opens behind any app window that is occupying the top-right of the desktop.

Is there a bug for this? I was ready to enjoy NOT having to re-start compiz after logging in.......

---

### Post by smsmith on 2010-12-20
Here's a bug I found on this.  I'm sure there are others.  My bug-fu is not very strong.  :p

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/691883](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/691883)

---

### Post by scradock on 2010-12-20
> **smsmith said:**
> Here's a bug I found on this.  I'm sure there are others.  My bug-fu is not very strong.  :p

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/691883](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/691883)
Thanks - I've confirmed the bug, as it appears to be describing the same fault that I see.

---

### Post by scradock on 2010-12-20
Update - the bug #691883 has now been marked as a duplicate of the (later) bug #692265, which does indeed seem to be the same problem.

Let's hope they fix one of them soon.......

---

