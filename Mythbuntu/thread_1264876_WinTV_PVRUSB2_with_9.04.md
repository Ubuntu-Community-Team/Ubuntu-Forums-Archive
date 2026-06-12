---
title: "WinTV PVRUSB2 with 9.04??"
date: 2009-09-12
forum: Mythbuntu
---

### Post by grenloch101056 on 2009-09-12
long time lurker, first time poster

I've been running 8.10 since april without a hitch, my database became corrupted so I upgraded to 9.04.  Everything is going well except for my PVRUSB2.  It works but only on the same channels that are available OTA, with 8.10 it worked for all the basic cable channels.  In the backend setup when i do a channel scan it defaults to US-Bcast instead of cable, I can change it and it recognizes all the proper channels like it did in 8.10.  When I turn to them all I get is snow and no audio.  Any suggestions??  Thanks in advance for your help.

update: When looking though the logs i see "not IVTV Driver?"  right after connecting to the backend's database, is this my issue???

---

### Post by danbodoh on 2009-09-13
"Not IVTV Driver?" is not a problem; it's always in the logs.

---

### Post by grenloch101056 on 2009-09-13
> **danbodoh said:**
> "Not IVTV Driver?" is not a problem; it's always in the logs.

thanks for your reply, i feel like an idiot, In my backend setup I had selected broadcast instead of cable for modulation type.  Once i changed that it worked fine

---

