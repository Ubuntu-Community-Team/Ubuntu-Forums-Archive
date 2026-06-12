---
title: "[SOLVED] How do I start backend remotely?"
date: 2008-12-02
forum: Mythbuntu
---

### Post by SiHa on 2008-12-02
I've got ACPI Auto-shutdown / wakeup sorted (I think).

Essentially the combined BE/FE machine is on all day, shuts down automatically sometime after 23:00 and comes back on at 07:00.

It occurred to me last night, what happens if I want to turn the TV on in the middle of the night? I ask becuase we're expecting a happy event in a couple of weeks!

The Mobo is capable of Wake-on-Lan, but I have no idea how to achieve this (simple ?) task.

Any advice appreciated, TIA

Edit: Found 'wakeonlan', installed it, checked the MAC address of the backend, shutdown, type wakeonlan <mac address> and it worked!

First time!

Nothing in Linux works first time!

Wow.

---

### Post by jMon54 on 2008-12-02
[FONT="Comic Sans MS"][SIZE="4"][SIZE="5"][COLOR="Blue"]Congratulations![/COLOR][/SIZE][/SIZE][/FONT]

---

### Post by SiHa on 2008-12-03
Thanks. I haven't tried getting the frontend to wake the backend automatically yet, but I'm hoping that's the simple bit.

---

