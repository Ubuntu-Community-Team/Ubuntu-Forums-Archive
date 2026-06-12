---
title: "Karmic: Cannot log in - NTP server problem"
date: 2009-10-19
forum: Mythbuntu
---

### Post by GuiGuy on 2009-10-19
First off, I note that after a clean install the initial 'Grub Loading" message doesn't appear so there seems no way to go to a system restore. 

Second, when the pc starts up I get a continuous loop messaging "Stopping NTP Server", "Done", "Starting NTP Server", "Done". 

Eventually a login prompt appears, but it is impossible to enter a login sequence because of the NTP server stopping and starting. 

I can see no way of breaking into the start up sequence to resolve this. So it looks like a re-install unless someone's got a suggestion?

Thanks

---

### Post by GuiGuy on 2009-10-19
Nevermind, I've decided to re-install and disable the NTP server this time.

---

### Post by nickrout on 2009-11-09
> **GuiGuy said:**
> Nevermind, I've decided to re-install and disable the NTP server this time.

Not such a good idea. Myth needs an accurate clock for scheduling etc.

---

