---
title: "Cursor gone after hibernate"
date: 2012-10-13
forum: Multimedia Software
---

### Post by jolindbe on 2012-10-13
I've just upgraded from 10.04 to 12.04 (32-bit), and one of the several glitches I've discovered so far is that after suspend the mouse pointer goes invisible. The mouse still works - I can click and hover and so on, but I can't see the cursor!! This is of course extremely annoying, and the only "solution" I've found yet is reboot.

I am running a Lenovo Thinkpad T410, with Nvidia graphics, and I read somewhere that this might be related to the graphics card, which is why I'm posting here. Any solutions?

---

### Post by jolindbe on 2012-10-14
Anyone? Is there anywhere I can even start looking for what's wrong?

---

### Post by jolindbe on 2012-10-15
Update: I realised that movement of the invisible mouse is restricted to the lower 60-70% of the right edge of the screen - if the desktop is up I can get a right-click menu, but only in these positions.

I also managed to start Nvidia X Server Settings, and doing so, I found that the X Server Display Configuration Layout was empty. I clicked "Detect Displays" ("clicked" as in "went there with the keyboard"), and my screen popped up. I still couldn't "apply", so I changed the resolution from the correct one to "Auto". Then I applied, and my cursor is back.

Of course this is an improvement, I no longer have to reboot to get the cursor back, but going into Nvidia X Server every time I suspend is somewhat annoying (yes, I realised that it is "suspend" and not "hibernate" I am recovering from, sorry about the confusion).

Any theories from this info?

---

### Post by jolindbe on 2012-10-15
Update again: This only occurs if I suspend the computer by closing the lid, not if I suspend it from the shutdown menu.

What happens when I resume after a close-lid-suspend is that I get the password screen, and see the mouse cursor, and can move it, for 1-2 seconds. Then, the screen flashes (black), then back to password screen, but cursor is gone.

---

### Post by jolindbe on 2012-10-15
Update again: Executing xrandr -s 1 (which is the resolution settings for my screen) gives the cursor back. As far as I understand, it is all about some kind of updating the X interface. Now I am just hoping for somebody who can give me a pointer on how to do that automatically after a suspend. But it seems a bit silent here...

---

