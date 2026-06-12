---
title: "How do I change resolution via terminal? Out of range after enabling ATI restricted."
date: 2008-06-22
forum: Multimedia Software
---

### Post by SlaughterDog on 2008-06-22
I just installed Ubuntu. After enabling ATI restricted drivers, it defaults to a resolution out of range. How can I fix this?

Even when using gnome failsafe session, I can't choose the proper 1280x1024 resolution that I should get in the GUI list. I don't know how to change any of this manually.

---

### Post by Cilionelle on 2008-06-22
Hi!  Don't know if this thread will help you in your troubles, but this is the help I got.  [http://ubuntuforums.org/showthread.php?t=470421](http://ubuntuforums.org/showthread.php?t=470421)

Try 'sudo dpkg-reconfigure xserver-xorg' if you haven't already and follow the prompts, going with the default if necessary.  On the page where you can choose the resolution modes X will use, choose a couple that fit and then finish the configuration program.  Then restart X (by either restarting your comp or (if you're in the "terminal" pre-GUI) typing 'startx'.

---

### Post by SlaughterDog on 2008-06-22
Well I hooked it up to the TV, and changed the resolution to 1280x1024 and it works now... however, now the login screen res is out of range.

So, I just need to set the login screen resolution. How do I do that?

---

