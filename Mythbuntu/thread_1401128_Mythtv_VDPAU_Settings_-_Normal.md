---
title: "Mythtv VDPAU Settings - Normal"
date: 2010-02-07
forum: Mythbuntu
---

### Post by chetldr on 2010-02-07
I accidentally erased the default settings.  Can someone post for me?

Thanks...

---

### Post by cedyathome on 2010-02-10
It isn't often that I can contribute here 

If rez >= 0 720 - vdpau & vdpau
Decoder nvidia vdpau acceleration
Video / os renderers - vdpau
Primary deinterlacer Temporal 2x, hw
Fallback deinterlacer Temoral 1x, hw
Custom filters colorspace=0


If rez >= 0 0 - vdpau & vdpau
Decoder nvidia vdpau acceleration
Video / os renderers - vdpau
Primary deinterlacer Advanced 2x, hw
Fallback deinterlacer Advanced 1x, hw
Custom filters colorspace=0

---

