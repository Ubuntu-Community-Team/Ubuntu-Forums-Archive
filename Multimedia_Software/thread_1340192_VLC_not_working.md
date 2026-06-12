---
title: "VLC not working"
date: 2009-11-28
forum: Multimedia Software
---

### Post by paulruscito on 2009-11-28
u9.10 . I did a clean install of VLC. I changed the device it's searching in the Disc options of the media tab in VLC to /dev/dvd. It's been a week and I can't get a DVD to play. Is it really this hard?

No error messages the dvd spins and then nothing happens. DVD stops spinning.

---

### Post by andrew.46 on 2009-11-28
Hi paulruscito,

> **paulruscito said:**
> u9.10 . I did a clean install of VLC. I changed the device it's searching in the Disc options of the media tab in VLC to /dev/dvd. It's been a week and I can't get a DVD to play. Is it really this hard?

Can you run your dvd from the commandline as follows:

```
cvcl -v dvd://
```

and post the full commandline + terminal output? This should reveal any libdvdread, libdvdcss, video out and audio out error messages.

Andrew

---

