---
title: "Logitech Quickcam IM - Can't record video"
date: 2007-09-29
forum: Multimedia &amp; Video
---

### Post by kallistra on 2007-09-29
I can get my camera to take snapshots but I can't get it to take video properly. I've tried cheese and xawtv for a few apps. It's fairly frustrating. I've included some extra info below if anyone can help me.

lsusb info
```

Bus 005 Device 002: ID 413c:a005 Dell Computer Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 062a:0000 Creative Labs Optical Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:08d9 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

```My error in dmesg is the following:

```

[ 1175.924000] ubuntu/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (11)

```Any suggestions appreciated.

---

