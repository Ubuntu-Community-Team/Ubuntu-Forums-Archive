---
title: "'Skip ahead' hangs front-end?"
date: 2009-11-30
forum: Mythbuntu
---

### Post by movieman on 2009-11-30
Anyone know why 'skip ahead' typically causes the front-end on my netbook to hang? Worse than that, the 'close' option isn't even available if I click on the taskbar icon, so the only way to kill it is to log out, reboot or manually from the command line.

It's not the network because I can still ping the backend and I can see the NFS-mounted recordings with 'ls'.

The frontend.log file is full of 'Error: Video frame buffering failed too many times' messages: so it's still running but not interacting with the mouse or keyboard anymore.

---

### Post by ian dobson on 2009-11-30
Hi,

What decoder are you using? I've seen mythfrontend lockup when doing fastforward when using the software decoder (ffmpeg?).

Regards
Ian Dobson

---

### Post by movieman on 2009-11-30
To be honest, I've no idea: I just installed it with the default settings.

---

### Post by gwagchunks on 2009-11-30
> **movieman said:**
> To be honest, I've no idea: I just installed it with the default settings.

I had similar issues, not on a netbook though. I went into mythbuntu control center / advanced management and selected MySQL / Optimise Tables

There is also an option to do this via mythweb (it has a few more options)

Seemed to do the trick for me

---

### Post by SiHa on 2009-11-30
> **ian dobson said:**
> Hi,

What decoder are you using? I've seen mythfrontend lockup when doing fastforward when using the software decoder (ffmpeg?).

Regards
Ian Dobson

Just seen this for the second time today, using ffmpeg, on my BE/FE. That machinbe isn't VDPAU-capable, and I long ago gave up with XVMC.

mythfrontend.log
```
Waited too long for video to pause
.
.
.
 
```repeated every 300ms or so for about 6 hours

Any ideas? Didn't happen with 0.21.

---

