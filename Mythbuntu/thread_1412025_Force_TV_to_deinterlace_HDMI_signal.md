---
title: "Force TV to deinterlace HDMI signal?"
date: 2010-02-20
forum: Mythbuntu
---

### Post by cedyathome on 2010-02-20
I am not satisfied with the quality of HD display on my TV, and got to thinking - is there a way to force the TV to do the de-interlacing? It deinterlaces QAM signals really well, so why not let it de-interlace the HDMI signal? 

I removed the deinterlace filters in MythTV (still using VDPAU) and the results were horrible! 

I don't know enough about HDMI, X and Linux to know if this is possible. And if so, what would I need to do?

My hardware:
Video chip: NVidia 8200 on ASUS motherboard. Assigned 512MB in bios.
Processor : AMD Athlon 64 2.7 GHz. Processor speed set to 2.4GHz.
Memory 2GB.

I am using Mythbuntu 9.10 and have upgraded to the 195.xx nvidia driver using the JVA repo.

Any help is appreciated, including pointers to sites that I can learn from.
Thank you.

---

### Post by nickrout on 2010-02-20
what resolution are you driving the tv at? 1080p? 1080i? 720p?

---

### Post by cedyathome on 2010-02-20
The TV's "native resolution" is 720p.  I assume that the I am driving it at that resolution. How do I figure that out?

I was thinking if I could drive it at 720i, it could handle the deinterlacing. However, I don't **know** that it can, and was hoping someone here would have the answer.

TV is a Samsung LN32A450

---

