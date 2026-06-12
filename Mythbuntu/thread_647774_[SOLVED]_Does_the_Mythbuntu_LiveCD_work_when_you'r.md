---
title: "[SOLVED] Does the Mythbuntu LiveCD work when you're only using TV out, no VGA?"
date: 2007-12-22
forum: Mythbuntu
---

### Post by Levander on 2007-12-22
I'm trying to reinstall Mythbuntu Gutsy on my PC.  I've only got my video card hooked up to it's monitor via a component cable coming out of the TV out port.  

It boots okay, but where I'm supposed to see the GDM login screen, instead I see a black screen with a vary narrow band across the top.  When I move my mouse around and get it inside that little band, I can make out where I can see the mouse pointer moving around.

No errors in /var/log/Xorg.0.log.  The only thing I see at the bottom of /var/log/gdm/:0.log is a message about the screen not being DRI capable.  But, I don't know that that's an error.  Is there somewhere else to look for log messages?

Ideas for where to go from here?  Does my graphics card have to be hooked up via a VGA cable for the Mythbuntu LiveCD to work?

---

### Post by rachus on 2007-12-23
I have the same question, however I'm only using S-Video out the back of an nVidia FX5800 -- and no bands at the top or anything in X, I can Ctrl+Alt+F1...F7 to another TTY, but X is no go except using the Safe graphics setting at the LiveCD splash.

---

### Post by Levander on 2007-12-23
Yeah, I finally figured this out last night.  The Mythbuntu LiveCD uses the open source nv driver, which doesn't support TV out.

You just use safe graphics mode to start X with the Mythbuntu LiveCD, like you said.

---

### Post by Levander on 2007-12-23
How do I mark a thread SOLVED?

---

