---
title: "Welcome back type sound when screen saver disabled"
date: 2009-04-21
forum: Multimedia Software
---

### Post by zigga15 on 2009-04-21
Hey guys,

Bit of a random question. I want ubuntu to make a "welcome back" sound when the screensaver is de-activated (or if the mouse is moved when the monitors are on standby).

I have googled around a bit and couldn't find much. I am just wondering where to start, I was thinking about polling for mouse movement events when the screen saver was active and then "interposing" something to do this. Any hints would be great :)

Regards,

~ Dan

---

### Post by kostkon on 2009-04-21
You could write a small daemon that listens to the *SessionIdleChanged* D-Bus signal of the *org.gnome.ScreenSaver* object (i.e. the screensaver) and then plays a sound using for example *aplay*.

---

