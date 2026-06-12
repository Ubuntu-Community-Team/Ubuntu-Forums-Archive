---
title: "Network interface stuck active on sleep/shutdown"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by ThatGuyOverThere on 2009-03-14
Setting up a multiple boot with ubuntu ibex x64 on a vista x64 HP slimline with Irvine-GL6E mainboard (Realtek RTL-A210 LAN).

When ubuntu shuts down or sleeps, it leaves the LAN router's link light on, which may be part of the functionality for wake-on-lan.  There is no bios setting to disable that for this mainboard.

In vista's Device Manager, there are network interface card options where the interface power can be turned off, and with those settings, a boot/shutdown cycle through vista clears up this problem ( or "feature" ) until the next time ubuntu boots.

Is there something I can change in ubuntu's halt script or elsewhere to drop the network interface link on sleep or off?  (not an expert, but maybe someday)

---

### Post by ThatGuyOverThere on 2009-03-19
Still stumped on this one.  Even trying to sift through old threads here is turning up nothing, or I don't know what to look for.

Lots of threads on wireless problems, though.  Glad I'm not using wireless!

Let me see if I can clarify my question:

How can ubuntu be told to turn off the power of the wired network interface (NIC) when shutting down or sleeping?

Of course, it would then need to be able to turn it back on when booting or waking.

Must be plenty of people here for whom this is an easy one to tackle.

---

### Post by osusoy on 2010-05-15
Having the same problem, disappointed that there are no good solutions anywhere as this is a fairly serious problem; the active network card blocks the routers and makes the whole network unusable for me :(

This only started happening for me with Karmic and is still a problem with Lucid. A temporary workaround is to set static IP and purge Network Manager. Hope this works for you too in the meantime but it would be good to hear from someone who knows how to make Network Manager do the right thing.

---

### Post by cariboo on 2010-05-16
Have either of you checked to see if a bug has been created? If there isn't please create one.

If the devs don't know about a problem, that can't fix it.

---

