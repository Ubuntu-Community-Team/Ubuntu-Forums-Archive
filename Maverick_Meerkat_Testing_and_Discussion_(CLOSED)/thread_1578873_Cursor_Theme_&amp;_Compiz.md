---
title: "Cursor Theme &amp; Compiz"
date: 2010-09-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by cottfcfan on 2010-09-21
Has anybody managed to change the cursor theme with compiz running.
With no Visual Effects its fine. With Compiz it just keeps defaulting back to DMZ-Black.

---

### Post by cottfcfan on 2010-09-22
Bump....
Am I the only one with this issue?

---

### Post by wacked_up on 2010-09-22
Try installing compiz-config-settings-manager. In it, I remember there is a setting somewhere about the used mouse pointer. I think under "General" of "Gnome compatibility". That should fix your problem.

---

### Post by cottfcfan on 2010-09-22
Thanks Wackedup....
Its in General options in compiz-config-settings-manager.
You physically need to type in the name of your cursor theme, exactly as it appears in appearance preferences/Theme/Pointer.
Thats done the trick.
Thanks again.

---

### Post by jrothwell97 on 2010-09-22
Surely this qualifies as a bug, if to simply change the cursor theme you need to ignore the option for it in Appearance settings and then download additional software, fight through that and then type in the cursor name exactly as it appears?

IIRC I had this problem on Lucid (haven't had a chance to test on Maverick yet) so it's a relatively old bug - even though its [Launchpad bugs page](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/86184) lists as of my writing for it to have been fixed. (I'm changing the status of this bug to "confirmed" [**edit:** - done] so as to get the maintainers' attention.)

---

### Post by cottfcfan on 2010-09-22
I don't know if its a bug exactly, and its only when compiz visual effects are enabled. Its just that you have to change the cursor theme to the one your using, in Compiz settings manager.
 I think they've made some progress, because as far as i'm aware, there wasn't an option to do this in Compiz on Lucid.
Instead you had to edit the file /usr/share/icons/default/index.theme
 This way is much easier. As long as your aware how to do it of course, which I wasn't until a reply to this thread.

---

### Post by jrothwell97 on 2010-09-22
> **cottfcfan said:**
> I don't know if its a bug exactly, and its only when compiz visual effects are enabled. Its just that you have to change the cursor theme to the one your using, in Compiz settings manager.
 I think they've made some progress, because as far as i'm aware, there wasn't an option to do this in Compiz on Lucid.
Instead you had to edit the file /usr/share/icons/default/index.theme
 This way is much easier. As long as your aware how to do it of course, which I wasn't until a reply to this thread.

By any reasonable definition, though, it is a bug, since changing it in Appearance Preferences (which is where it *should* be) has no effect. From a user's point of view, there is no reason for there to be two separate interfaces for changing the cursor theme depending on whether you're running compiz or not.

---

### Post by cottfcfan on 2010-09-22
Looks like a fix has been pending for more than 3 1/2 years now so I wouldn't hold your breath.
At least there's a relatively simple workaround.

---

### Post by cottfcfan on 2010-09-22
Just an addition.
I just realized that any new programs you install use the Default cursor again, so you still have to edit the file I mentioned in post #6 to Inherits=cursorname
So not so simple after all.
3 steps are needed to change to a custom cursor in Maverick.

---

