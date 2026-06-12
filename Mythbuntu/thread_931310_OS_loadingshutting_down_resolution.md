---
title: "OS loading/shutting down resolution"
date: 2008-09-27
forum: Mythbuntu
---

### Post by darude on 2008-09-27
Is there a way I could set the screen resolution when Mythbuntu loads/shutdown?

I'm running the box on a 42" LCD TV and during startup, the TV keeps flashing **before** the mythbuntu start up/shut down screen appears.

On a standard 17" LCD monitor, I usually I see stuff like GRUB loading...., and at shutdown I see processes ended/killed. But I no longer see this on the 42" TV, instead I see annoying screen flashes. I suspect this is a resolution problem, does any one know how to fix this?

---

### Post by ian dobson on 2008-09-27
Hi,

I don't think so. Grub still uses the bios functions for screen display and until the system loads the graphical interface linux uses the resolution/configuration defined by the BIOS.

Unless you can hack/reconfigure you BIOS I don't think it'll be possible.

Regards
Ian Dobson

---

