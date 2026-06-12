---
title: "Audacity playback at 5x speed"
date: 2016-03-14
forum: Multimedia Software
---

### Post by ra7411 on 2016-03-14
[COLOR=#000000][FONT=Lucida Grande]I'm using audacity 2.1.2 with Ubuntu 15.10. I installed Audacity from a ppa, today.[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]It records streaming audio properly but the playback is about 5X the proper speed. I had the same problem with the prior version of audacity in Software Center, so I updated to this 2.1.2 version. Oddly, the prior version always played at a high speed - this version does too, but sometimes it will revert in the middle of a playback to the correct speed. I haven't messed with any of the settings on Audacity - it's running just as it installed. [/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]How do I fix this?[/FONT][/COLOR]

---

### Post by eezacque on 2016-03-15
> **ra7411 said:**
> [COLOR=#000000][FONT=Lucida Grande]I'm using audacity 2.1.2 with Ubuntu 15.10. I installed Audacity from a ppa, today.[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]It records streaming audio properly but the playback is about 5X the proper speed. I had the same problem with the prior version of audacity in Software Center, so I updated to this 2.1.2 version. Oddly, the prior version always played at a high speed - this version does too, but sometimes it will revert in the middle of a playback to the correct speed. I haven't messed with any of the settings on Audacity - it's running just as it installed. [/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]How do I fix this?[/FONT][/COLOR]

It's just another bug. In /usr/share/applications/audacity.desktop  replace Exec=audacity %F   with  Exec=env PULSE_LATENCY_MSEC=30 audacity %U

---

### Post by ra7411 on 2016-03-15
> **eezacque said:**
> It's just another bug. In /usr/share/applications/audacity.desktop  replace Exec=audacity %F   with  Exec=env PULSE_LATENCY_MSEC=30 audacity %U

Yeah - a bug or bugs that have been around a long time.  I've been trying to get this Audacity/Pulse combination to be dependable for a while. I think it's just a waste of time.

---

