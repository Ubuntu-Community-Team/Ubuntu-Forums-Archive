---
title: "Pulse Audio pausing music when switching users"
date: 2008-04-24
forum: Multimedia Software
---

### Post by darknuala on 2008-04-24
Whenever I am listening to Amarok, and my wife wants to switch over to her side to check her mail or whatever, the music that was playing will pause, once we click the switch users.  It will start back once I switch back over to my side.  I was told in the development forum that this was a 'feature'.  Is there a way to turn off this feature?

---

### Post by Greyfox_75 on 2009-05-14
Any one found a fix/switch for this?  I am running into this problem also.

/******EDIT******/
Found solution.  Edit /etc/default/pulseaudio
Change "PULSEAUDIO_SYSTEM_START=0" to "PULSEAUDIO_SYSTEM_START=1" and restart system works great.

---

### Post by krul on 2009-05-24
> **Greyfox_75 said:**
> Any one found a fix/switch for this?  I am running into this problem also.

/******EDIT******/
Found solution.  Edit /etc/default/pulseaudio
Change "PULSEAUDIO_SYSTEM_START=0" to "PULSEAUDIO_SYSTEM_START=1" and restart system works great.

Hi Greyfox,

I've tried this, but no luck. It seems ubuntu still creates a daemon per user. Did you changed besides this anything else?

---

