---
title: "sdpif is muted on restart"
date: 2012-10-01
forum: Mythbuntu
---

### Post by tdcarlo on 2012-10-01
Hi

Thanks to the help on this board I have been able to get sound out of HDMI from Mythbuntu 12.04.  I'm wondering if anybody can help me keep my spdif unmuted on restart.  After each restart, I have to open a terminal, run alsamixer, and unmute it again.  It's not a big deal but its hard to teach the 2 year old how to do this.  Is there a way around unmuting it each restart?

Thanks again...

---

### Post by nickrout on 2012-10-01
> **tdcarlo said:**
> Hi

Thanks to the help on this board I have been able to get sound out of HDMI from Mythbuntu 12.04.  I'm wondering if anybody can help me keep my spdif unmuted on restart.  After each restart, I have to open a terminal, run alsamixer, and unmute it again.  It's not a big deal but its hard to teach the 2 year old how to do this.  Is there a way around unmuting it each restart?

Thanks again...don't restart?

seriously, set them how you want them, then run

```
sudo alsactl store
```

Should save the settings to be applied on restart.

If for some reason that doesn't work, you could use alsactl to umute it in a script in /etc/rc.local, which gets run at the end of the startup sequence.

---

### Post by tdcarlo on 2012-10-01
Thanks...that worked.

I owe you a beer or something!

---

### Post by nickrout on 2012-10-01
I'll have one for you tonight.

---

