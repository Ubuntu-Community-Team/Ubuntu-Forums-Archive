---
title: "me-tv won't use multiple tuners"
date: 2010-08-02
forum: Multimedia Software
---

### Post by HRH_H_Crab on 2010-08-02
I have an hauppage dvb card with two DiBcom 3000 MC/P tuners showing up as /dev/dvb/adaptor0/frontend0 and /dev/dvb/adaptor1/frontend0.

These are visible under "devices" in me-tv so it knows about them.

The problem is, it will only use the first of these. I can't therefore record a show while watching another.

Here you can see the result of my attempt to change to the second adaptor manually:

```
Me TV 1.1.2
Me TV 1.1.2
02/08/10 19:46:00: Using /dev/dvb/adapter0/frontend0
02/08/10 19:46:00: Device: 'DiBcom 3000MC/P' (DVB-T)
02/08/10 19:46:02: Changing channel to 'BBC FOUR'
02/08/10 19:46:02: Frontend::tune_to(529833330)
02/08/10 19:46:02: Waiting for signal lock ...
02/08/10 19:46:02: Got signal lock
02/08/10 19:46:03: Channel changed to BBC FOUR
02/08/10 19:46:18: Using /dev/dvb/adapter1/frontend0
02/08/10 19:46:18: Device: 'DiBcom 3000MC/P' (DVB-T)
Xine engine terminating normally
```

Can anyone give me any pointers?

---

