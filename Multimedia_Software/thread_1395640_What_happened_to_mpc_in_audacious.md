---
title: "What happened to mpc in audacious?"
date: 2010-02-01
forum: Multimedia Software
---

### Post by acl123 on 2010-02-01
I used to be able to play MPC (musepack) in Audacious but can't any more.

I have the Audacious 2.1.1 package and libmpcdec3 installed, running Ubuntu 9.10

---

### Post by mc4man on 2010-02-01
It was removed due to some issues - as seen in changelog

> 
audacious-plugins (2.0.1-1) unstable; urgency=low
  * New upstream release.
    - New skins plugin with many less design flaws than the old XMMS code.
      (Closes: #456558, #460802, #500081)
    - Do not crash when invalid monkey's audio chunks are encountered.
      (Closes: #514674)
    
  * Acknowledge NMU, thanks Rafael for your work.
    - debian/patches/004-compile-with-libmtp8.patch: dropped,
      different patch integrated upstream to solve the same issue.
    
  * debian/audacious-plugins.install: add crossfade.so, skins.so.
  * debian/audacious-plugins-extra.install: add icecast.so, psf2.so, xsf.so
  * debian/control: enable projectm again.
  * debian/patches/*: dropped, integrated upstream.
  * debian/control: remove dependency on libmpcdec-dev and disable musepack
    support, as musepack sv7 and sv8 will be regained by audacious-ffaudio
    shortly, e.g. before squeeze ships.
    (Closes: #518679, #476383)

 -- William Pitcock <nenolod@dereferenced.org>  Fri, 29 May 2009 21:36:59 -0500

What audacious-ffaudio is I'm not sure other than it's not around here (ubuntu

---

