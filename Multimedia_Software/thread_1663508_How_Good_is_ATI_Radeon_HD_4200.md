---
title: "How Good is ATI Radeon HD 4200 ?"
date: 2011-01-09
forum: Multimedia Software
---

### Post by wbee on 2011-01-09
Hello,

((Yes,I searched here,but most of the responses are a couple years old,hence,the new post.))

The motherboard upgrade I'm considering has on board ATI Radeon HD 4200 graphics.

The manual for the board says that Hybrid Cross Fire is only supported on Windows Vista.((The manual copyright is two years old.))

Q: Is the on board 4200 good enough for viewing motion pictures from DVDs and sources like Hulu and You Tube,assuming adequate CPU and memory ? I do not play resource sapping games or edit motion pictures.

Q: If the 4200 is not good enough,do any open source Radeon drivers or furnished proprietary drivers support Hybrid Cross Fire function or would I need to plan on getting enough card to work without including the on board capacity in the calculation?

Thank you.

---

### Post by cascade9 on 2011-01-09
Flash has no hardware acceleration under linux, so things like Hulu and You Tube will be done by the CPU alone. Its possible that adobe will add hardware acceleration for linux flash in the future, but it will take a long while, if it ever happens. 

DVDs can be hardware decoding using the GPU (XvBA for ATI, VDPAU for nvidia) but XvBA is buggy. 

The only people who care about hybrid crossfire are very cheap gamers with windows. 

Since its a HD4200, I'm guessing that you are after an AMD CPU.  Even the slowest AM3 CPU should have enough power to play DVDs and flash videos. But a nice cheap nVidia GT210/GT220 and a AMD 770/870 chipset (no onboard video) might be a better idea than 785 chipset with an onboard 4200 IGP.

---

