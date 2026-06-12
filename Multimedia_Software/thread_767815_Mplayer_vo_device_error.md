---
title: "Mplayer vo device error"
date: 2008-04-25
forum: Multimedia Software
---

### Post by dbbolton on 2008-04-25
I can watch videos without problems with VLC and totem, but when I try to watch a video with mplayer, I get this error:

Error opening/initializing the selected video_out (-vo) device.

I went through the preferences and didn't see anything about -vo. Does anyone know how I can fix this?

---

### Post by Bubba64 on 2008-04-25
Have you installed Ubuntu restricted extras from add remove.

---

### Post by dbbolton on 2008-04-26
> **Bubba64 said:**
> Have you installed Ubuntu restricted extras from add remove.
Yeah

---

### Post by omicrondelta on 2008-04-26
> **dbbolton said:**
> I can watch videos without problems with VLC and totem, but when I try to watch a video with mplayer, I get this error:

Error opening/initializing the selected video_out (-vo) device.

I went through the preferences and didn't see anything about -vo. Does anyone know how I can fix this?

Use VLC or Totem then...

---

### Post by dbbolton on 2008-04-26
> **omicrondelta said:**
> Use VLC or Totem then...
That really isn't helpful at all. I'm not doing this for the purpose of watching videos, but rather simply to figure out why mplayer doesn't work.

---

### Post by mc4man on 2008-04-26
> I went through the preferences and didn't see anything about -vo.  Assuming your using gui under video tab is available drivers (-vo), try x11. Xv is preferred though, try running mplayer or gmplayer from cli and see what error mess. are

---

### Post by dbbolton on 2008-04-26
> **mc4man said:**
> Assuming your using gui under video tab is available drivers (-vo), try x11. Xv is preferred though, try running mplayer or gmplayer from cli and see what error mess. are
I tried the x11 driver and it works. Thank you very much.

---

