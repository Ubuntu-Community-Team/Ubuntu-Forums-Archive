---
title: "Intel GMA 950, Gigabyte GA945GM-S2 MB"
date: 2007-03-27
forum: Multimedia &amp; Video
---

### Post by dburnett77 on 2007-03-27
Would anyone happen to know how to increase the memory addressing for the GMA 950 onboard graphics for the Gigabyte GA-945GM-S2 motherboard?

It seems to be done via a driver for Windows, which of course I'm not running.  The only thing in the BIOS is for buffer, which is set at either 1MB or 8MB.

Also, in the device manager of Edgy, I see it, but no info on how much memory it's accessing.  Is there a way to see, adjust this via system utility?

Thanks.

---

### Post by dburnett77 on 2007-03-30
To answer myself, I found out in xorg.conf in the Driver section, you add a line:

VidoeRam    131072

to increase the default 12MB to 128MB in this instance.

---

