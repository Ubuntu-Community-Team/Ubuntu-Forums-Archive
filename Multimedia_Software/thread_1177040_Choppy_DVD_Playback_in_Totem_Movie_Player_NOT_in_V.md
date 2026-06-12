---
title: "Choppy DVD Playback in Totem Movie Player NOT in VLC"
date: 2009-06-03
forum: Multimedia Software
---

### Post by businessgeeks on 2009-06-03
Hello guys,

I am trying to play DVD on my Thinkpad X41 using Totem Movie Player via an external USB DVD drive. and Im getting very choppy video. 

I tried using VLC Player and playback was smooth. Anybody familiar with this problem?

---

### Post by psyke83 on 2009-06-03
> **businessgeeks said:**
> Hello guys,

I am trying to play DVD on my Thinkpad X41 using Totem Movie Player via an external USB DVD drive. and Im getting very choppy video. 

I tried using VLC Player and playback was smooth. Anybody familiar with this problem?

What graphics card have you got?

---

### Post by businessgeeks on 2009-06-03
> **psyke83 said:**
> What graphics card have you got?

I've got an Intel 915 graphics card.

---

### Post by psyke83 on 2009-06-03
> **businessgeeks said:**
> I've got an Intel 915 graphics card.

Are you using Jaunty (9.04)? If so, your MTRR range isn't set properly which is causing Totem to stutter (VLC and other applications are also affected, but it just so happens that Totem is more sensitive to this issue).

See my Intel graphics guide - you should follow only the "Safe" procedure, *or* alternatively, only use the fixmtrr.sh script.

---

### Post by businessgeeks on 2009-06-03
> **psyke83 said:**
> Are you using Jaunty (9.04)? If so, your MTRR range isn't set properly which is causing Totem to stutter (VLC and other applications are also affected, but it just so happens that Totem is more sensitive to this issue).

See my Intel graphics guide - you should follow only the "Safe" procedure, *or* alternatively, only use the fixmtrr.sh script.

Oh ok, will try that... getting really frustrated with jaunty though....

---

### Post by businessgeeks on 2009-06-03
Tried doing the safe configuration but with same results.

---

