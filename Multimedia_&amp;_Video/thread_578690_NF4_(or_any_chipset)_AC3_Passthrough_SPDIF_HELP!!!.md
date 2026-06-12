---
title: "NF4 (or any chipset) AC3 Passthrough SPDIF HELP!!!"
date: 2007-10-17
forum: Multimedia &amp; Video
---

### Post by Pinnocchio on 2007-10-17
Hi All

I've googled extensively and cannot find a working AC3 Passthrough ALSA configuration that works for SPDIF on the NF4 chipset (DFI Lanparty).

So my request is simple but in two parts:-

1.  Does ANYONE have AC3 passthrough working via SPDIF on their NF4 based chipset?  If so could you possibly post ALL your sound configuration files please.

2.  Does ANYONE have AC3 passthrough working via SPDIF on ANY chipset?  If so could you please post ALL your sound configuration files please......perhaps if we can get a library of what works we can make a working config for NF4.

Thanks in advance.

P

---

### Post by Pinnocchio on 2007-10-18
Bump

I'm really coming to the conclusion that AC3 passthrough just doesn't work at the moment (but nobody wants to admit it).

---

### Post by vsneaky on 2007-10-24
i'm having the same problem

---

### Post by iggee85 on 2007-11-09
It works for me. I'm using SPDIF optical out on an onboard Realtek ALC883. AC3-Passthrough won't work on any programs that use gstreamer though. So that means watching DVDs using totem-gstreamer won't give you AC3-Passthrough. You'll have to use totem-xine (Haven't tried it). There's some kind of design problem with gstreamer where it decodes AC3 into stereo before outputting to SPDIF.
Right now I'm using SMPlayer to watch DVDs and AC3-Passthrough works perfectly. There's even an option to use AC3-Passthrough over SPDIF in the configuration dialog so you don't have to pass it by command-line.

---

