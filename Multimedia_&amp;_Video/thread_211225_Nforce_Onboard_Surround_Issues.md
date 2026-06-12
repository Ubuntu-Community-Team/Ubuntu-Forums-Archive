---
title: "Nforce Onboard Surround Issues"
date: 2006-07-08
forum: Multimedia &amp; Video
---

### Post by einhander on 2006-07-08
Hi all,

I've read through several guides and how-to's about getting the onboard surround to work on Nforce chipset motherboards, and have had no luck thus far.

The installation had no errors, but trying to blacklist snd_intel8x0 has given me problems. I've tried placing the configuration in several places in /etc/modprobe.d/ but I still get an error with the xine engine when I open amaroK telling me that xine was unable to initialize playback.

I've created a file, "nforce" in the /etc/modprobe.d/ directory with "alias sound-slot-0 nvsound" as well.

Any help would be greatly appreciated.

---

