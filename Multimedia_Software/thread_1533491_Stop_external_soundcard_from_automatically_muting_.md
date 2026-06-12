---
title: "Stop external soundcard from automatically muting after suspend"
date: 2010-07-18
forum: Multimedia Software
---

### Post by TechBeastie on 2010-07-18
Hi everybody,
  I have an external (USB) sound-card attached to my laptop, through which I generally want all of my sound routed.  By and large, the device works wonderfully - with one minor (but annoying) quirk: every time the computer reawakens from suspend mode with the device plugged in, something in the OS automatically mutes all sound coming from that device.  Note that Ubuntu does NOT restore control to my on-board sound chip - so whenever this happens, I'm left with a machine that's basically universally muted, for no good reason. Of course, I can just go into the volume control panel and unmute the external card - but I'm getting a bit tired of having to do this each time I turn on the machine.  

Anybody have any ideas as to how I can force Ubuntu to NOT mute the external card?  

Thanks!

---

### Post by v2graeme on 2010-10-26
To add my 2 cents - I also have this issue and would appreciate any help to resolve.

---

### Post by juliansuddaby on 2010-12-02
Bump -- I also have this problem and wonder if anyone's found a way to fix it. Suspend mutes not only output, but also the microphone as well, so it's doubly inconvenient.

---

### Post by juliansuddaby on 2010-12-06
Ah, stumbled on the fix.

This is a deliberate feature, and I think it makes sense to be the default behavior. If you want to change it, edit the file /usr/lib/pm-utils/sleep.d/01PulseAudio and find the lines

```
mute_pulse sink "${THIS_USER}"
mute_pulse source "${THIS_USER}"
```

Comment these out and you'll no longer get muted sound after a suspend or hibernate.

---

