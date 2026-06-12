---
title: "Emapthy crashes"
date: 2010-08-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jerrynewt on 2010-08-21
Anyone else having empathy crashing lately?? I click on the chat icon and the contacts box comes up for bout one half second and disappears.

---

### Post by jerrynewt on 2010-08-22
bump**

---

### Post by BCurtisWX on 2010-08-22
What version of Ubuntu are you using?  What version of empathy are you using?

---

### Post by VinDSL on 2010-08-23
> **jerrynewt said:**
> Anyone else having empathy crashing lately??I only ran Empathy for a few minutes, on 10.10.

I dunno.  I've tried to have empathy for Empathy, but...

You might try starting Empathy from CLI.  That way, when it crashes, the resultant text in the terminal should give you a clue as to what's happening.

Probably a segfault, or such...

---

### Post by kyleabaker on 2010-08-23
> **jerrynewt said:**
> Anyone else having empathy crashing lately?? I click on the chat icon and the contacts box comes up for bout one half second and disappears.

Its been crashing more lately than usual, but I haven't noticed any specific crashers. Care to go into a little more detail?

Ubuntu 10.10 x86_64 here with all updates installed.

---

### Post by jerrynewt on 2010-08-26
Installed telepathy-logger and all is well in UbuntuLand!!

---

### Post by kyleabaker on 2010-08-26
> **jerrynewt said:**
> Installed telepathy-logger and all is well in UbuntuLand!!

So the crashes were due to telepathy-logger not being installed?

---

### Post by lsrg on 2010-09-01
> **kyleabaker said:**
> So the crashes were due to telepathy-logger not being installed?
Yes!

the error message was:
GLib-GIO-ERROR **: Settings schema 'org.freedesktop.Telepathy.Logger' is not installed

aborting...
Trace/breakpoint trap (bolcat de la imatge del nucli)

---

