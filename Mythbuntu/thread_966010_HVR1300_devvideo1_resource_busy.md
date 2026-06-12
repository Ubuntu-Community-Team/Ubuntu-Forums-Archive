---
title: "HVR1300 /dev/video1 resource busy"
date: 2008-11-01
forum: Mythbuntu
---

### Post by rogers21 on 2008-11-01
I have a HVR1300 card which I have downloaded and installed the latest v4l modules.  The DVB card part is working perfectly same with the /dev/video0 raw part.  However when I go to access the mpeg card via /dev/video1 I get in the mythbackend.log:-

```
2008-11-01 14:44:22.415 Channel(/dev/video1)::Open(): Can't open video device, error "Device or resource busy"
```

Any help appreciated.

Cheers

---

### Post by ian dobson on 2008-11-01
Hi,

What happens if you shutdown mythbackend then do a cat /dev/video1 > test.mpeg and then ctrl C to stop saving.

What does a lsof /dev/video1 display?

Regards
Ian Dobson

---

