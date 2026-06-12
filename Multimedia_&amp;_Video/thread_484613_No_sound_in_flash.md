---
title: "No sound in flash"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by Anarchy965 on 2007-06-26
The onboard sound is working on my motherboard in ubuntu. But I'm still not getting any sound in flash on sittes like youtube. Does anyone know how to fix this?

edit: The onboard sound is the NVidia CK804 from my ASUS A8N32-SLI Deluxe mobo. I've tried setting the "FIREFOX_DSP=" variable in the "/etc/firefox/firefoxrc" file to several different things including "none", "aoss", and even "Nvidia CK804", but I haven't gotten any results. I've also tried a few other methods of fixing this problem that have worked for other people, but like I said, no results...

---

### Post by deadgobby on 2007-06-26
Do you have a other sound card?  Oh lets say Sound Blaster for example? If you have like a SB card and want to play every thing through that card. Then you need to go into your BIOS and disable on board sound card. Then all sounds will play through that card. Now if your only sound is from the on board. The chip set may be a Intel 8x0 chip set. With the Intel chip sets there is some bugs to dig through. Are you using a LT. If a LT what is your LT make and model? Thus the debugging fun has started.
Gobby

---

### Post by Anarchy965 on 2007-06-26
> **deadgobby said:**
> Do you have a other sound card?  Oh lets say Sound Blaster for example? If you have like a SB card and want to play every thing through that card. Then you need to go into your BIOS and disable on board sound card. Then all sounds will play through that card. Now if your only sound is from the on board. The chip set may be a Intel 8x0 chip set. With the Intel chip sets there is some bugs to dig through. Are you using a LT. If a LT what is your LT make and model? Thus the debugging fun has started.
Gobby

I have another sound card(EMU 1212m), but it is not supported in ubuntu. That's why I'm using my onboard audio for now. The chip set isn't an intel chipset. like I said the chipset controlling the onboard sound is the NVidia CK804 SLI chipset. To make it clear: The sound works fine everywhere else but in flash. What is an LT?

---

### Post by deadgobby on 2007-06-27
LT stands for Lap Top

---

