---
title: "broadcom b43 wont turn on/ recognize wireless signals"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by aloha13 on 2010-11-21
So I just loaded ubuntu 10.10....and it works great...except for my wireless

i've got a broadcom b43 ...i went into system, administration, download additional drivers and downloaded/authenticated a b43 driver, but my machine (hp dv4405) does not recognize any wireless signals.  The wireless light on my computer doesnt turn on (there's a button to turn it on and off) anyways...it's annoying. I guess broadcom recently released some open source drivers, but I'm having trouble sorting through all the info...any advice would be appreciated as I'm new to this OS. thanks

---

### Post by uncaspi on 2010-11-21
Open a terminal and type sudo rfkill unblock wifi
and see if the radio is turned on. So we take it from there.

---

### Post by aloha13 on 2010-11-21
good stuff...only, i'm so new i don't even know what 'open a terminal' means...can you clarify?

---

### Post by uncaspi on 2010-11-21
Click upper left panel I think it's Applications. I don't have English language so click upper left panel next to ubunto icon. Then selct Assessories and then terminal or console.

---

