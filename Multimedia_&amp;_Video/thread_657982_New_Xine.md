---
title: "New Xine"
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by Mark76 on 2008-01-04
Okay, so I found that there have been many updates to Xine since the versions in the repos  (that's on 0.5.5, the newest is 1.8). Anyway, I've had problems with streams in Xine which I figure using the newest version might solve, so I download the tar.gz file from the Xine site, open a terminal in the extracted folder and run ./configure.

And this is what I get at the end

> WARNING! No X11 output plugins will be built.

For some reason, the requirements for building the X11 video
output plugins are not met. That means, that you will NOT be
able to use the resulting xine-lib to watch videos in a window
on any X11-based display (e.g. your desktop).

If this is not what you want, provide the necessary X11 build
dependencies (usually done by installing a package called
XFree86-devel or similar) and run configure again.

So, naturally, I open up synaptic and search for "xfree86" and, you know what?  I don't find xfree86. Not even XFree86.  So I go off to Google it and, yeah, I find it but it's like a load of confusing options and clicking on any of them just leads to more confusing options. So I really don't know what to do.

So tell me.

Thanks

---

### Post by yopnono on 2008-01-04
What version of ubuntu are you running?

On the 7.10 the xine lib is 1.1.8 = latest

---

### Post by Mark76 on 2008-01-04
I'm running 7.10 on AMD64.

I have libxine 1.1.7

So why does trying to play BBC News 24 tell me I don't have the sipr.so and drvc.so plugins?

---

### Post by yopnono on 2008-01-04
Install xine-plugin and try.
Anyhow I don't run 64 I'm on 32.

---

### Post by yopnono on 2008-01-04
Add the backports to the synaptic aswell

---

