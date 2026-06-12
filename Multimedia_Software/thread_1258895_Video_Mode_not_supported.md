---
title: "Video Mode not supported"
date: 2009-09-05
forum: Multimedia Software
---

### Post by galvao on 2009-09-05
Greetings.

I'm having  a problem when running some games (like, for an example, SuperTux 2 and Urban Terror):

When the video mode is switched I get a "Video mode not supported" message. Is there a way to solve this (either per game or globally)? 

TIA,

---

### Post by xc3RnbFO8P on 2009-09-05
I am not sure, you can try to add it in xorg.conf:
Option "ModeValidation" "NoXServerModes"

---

