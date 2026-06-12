---
title: "Is the &quot;nvidia-glx-new&quot; package always up-to-date?"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by kcy29581 on 2007-10-16
Hi all,

Searching for "nvidia" in Synaptic yields the following drivers, obviously depending on the hardware used:
[LIST]
[*]nvidia-glx: NVIDIA's 9000-series drivers
[*]nvidia-glx-legacy: NVIDIA's 7000-series drivers
[*]nvidia-glx-new: NVIDIA's 100.xx.xx-series drivers[/LIST]Please correct me if I'm wrong, but I believe (from experience with Ubuntu) that the nvidia-glx and nvidia-glx-legacy packages never get updated if a new 9000 or 7000-series driver is released, during the lifecycle of a Ubuntu release; they get updated when a new Ubuntu release comes along (for example, the versions of the aforementioned packages stay the same during Feisty, but they may get updated when Gutsy is released, if updates are available from NVIDIA).

My question regards the nvidia-glx-new package; does this package follow the same rules as the aforementioned packages? Currently Gutsy has the 100.14.19 driver available; does this mean that:
[LIST]
[*]Gutsy will always have 100.14.19, or
[*]does the "-new" suffix mean that every time the 100.14.xx-series drivers are updated by NVIDIA, Ubuntu will also update the "nvidia-glx-new" package[/LIST]I have always used the drivers straight from NVIDIA's site, so if the "nvidia-glx-new" package is always up-to-date, then that would be very helpful.

Thanks.

---

### Post by FredB on 2007-10-16
I think drivers will be updated if there is more interest and not to risky. I use nvidia-glx-* packages since dapper and no problem... So... ;)

---

### Post by kcy29581 on 2007-10-16
I love always using the latest drivers, don't ask why cause I don't know myself!

I might just install the "nvida-glx-new" package now anyway, since this is just a test installation for Gutsy, and hopefully someone who knows 100% will answer the question.

Would submitting a question in Launchpad be a good idea?

---

### Post by MindFlayer on 2007-10-16
I'd like to be able to use the latest drivers possible since they're almost always better than the older ones, at least for newer nVidia cards. In fact, I couldn't run Feisty because the drivers it came with didn't support my Geforce8800 GTS and I didn't want to use envy... :(

---

### Post by TNakos on 2007-10-16
i have had no problems with the nvidia-glx-new driver pack. i found it better than the old one

---

### Post by TNakos on 2007-10-16
oh i never tried legacy

---

### Post by BoardDWorld on 2007-10-16
It wouldn't hurt to run the "nvidia-glx-new" package and compare the driver version with nVidia's current version. I'm interest in knowing the results as I will be doing a full convert to Ubuntu when 7.10 is released, Vista's going to be reduced to a VM:grin:.

---

### Post by IanW on 2007-10-16
Current;y, nvidia-glx-new under Gutsy definitely carries Nvidia's current release of 100.14.19 (I'm using it right now).

---

### Post by mc4man on 2007-10-16
I'm using 100.14.19+2.6.22.4-14.8 which other being a pita to set proper refresh rate for the res. I use works great. An update just became available - 100.14.19+2.6.22.4-14.9 which i'll pass on till thurs. - don't like to fix what isn't broke

---

