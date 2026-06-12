---
title: "Computer becomes unresponsive when running Unity"
date: 2010-08-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by zekopeko on 2010-08-03
I get heavy disk use and shortly after that the whole computer stalls. I can't even get to the terminal via Ctrl-Alt-F1.

Anybody else experience this? I don't see this happening on the regular desktop edition. Running Unity on an Asus 1000H.

---

### Post by cariboo on 2010-08-03
I get the same thing after upgrading this morning, there is lots of fancy new stuff, but it seems to be very slow.

I'm running a Compaq Mini 110.

---

### Post by MacUntu on 2010-08-03
This will hopefully go away soon: [https://bugs.launchpad.net/unity/+bug/599425](https://bugs.launchpad.net/unity/+bug/599425)

Especially working with maximized windows leads to CPU thrashing sometimes (6600 GT, Nvidia's BLOB). I'm not seeing any unusual I/O loads, though.

---

### Post by zekopeko on 2010-08-03
> **MacUntu said:**
> This will hopefully go away soon: [https://bugs.launchpad.net/unity/+bug/599425](https://bugs.launchpad.net/unity/+bug/599425)

Especially working with maximized windows leads to CPU thrashing sometimes (6600 GT, Nvidia's BLOB). I'm not seeing any unusual I/O loads, though.

Well I did notice that playing with Totem results in Mutter using 40-50% of my CPU but that is apparently getting fixed.

Prior to 0.2.22 I noticed my disk light being constantly on and then the whole computer would simply stop to a crawl. I  couldn't even move the mouse. So far it is looking better but I will keep monitoring before reporting a bug.

EDIT: Crap, I just got hit again. Barely made it to the terminal. Looks like Chromium was mostly trashing the disk but it was only a few MBs read/write. I really don't know what is happening here. Looks like it gets trigger by mousing over the launcher. Maybe I'm getting hit by a variant of the Quicklist memory leak bug?

---

### Post by MacUntu on 2010-08-03
Yeah, that leak desperately needs a fix. As soon as the swapping starts, the session is toast on my machine. Have you checked your RAM usage?

---

