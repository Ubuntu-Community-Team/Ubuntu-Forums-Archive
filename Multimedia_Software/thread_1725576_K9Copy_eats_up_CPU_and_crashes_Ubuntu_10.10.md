---
title: "K9Copy eats up CPU and crashes Ubuntu 10.10"
date: 2011-04-09
forum: Multimedia Software
---

### Post by dindoliya on 2011-04-09
I am new to ubuntu and am loving it so far. However, this is a deal breaker issue for me. If I use K9Copy to compress a 6.4 gb DVD to a 4.4gb ISO files, it heats up the CPU and the machine shuts off. When I do this with system monitor ON, I see 160% to 180% CPU usage. I guess this is due to dual core on my Gateway laptop.

Then I installed DVD Shrink and tried the same by running DVD Shrink using Wine. This caused the same problem.

I did not have this issue when I was using Windows Vista. Is there anything that I can do to avoid this problem?

Thanks,

---

### Post by dindoliya on 2011-04-10
Thinking that 64 bit may help encoding operations, I installed 64 bit ubuntu today. It worked well upto 60% completion (better than before) before it heated up the laptop enough for it to switch off.

---

### Post by inobe on 2011-04-10
do you use a cooler?

not stating that it has anything to do with shutdowns, just wondering.

side note: i have dusted out many of laptops, none were pretty, basically all heat sinks get crammed with dust and eventually get hot.

they are tough to clean, it involves disassembly of the laptop.

---

### Post by alphacrucis2 on 2011-04-10
> **dindoliya said:**
> Thinking that 64 bit may help encoding operations, I installed 64 bit ubuntu today. It worked well upto 60% completion (better than before) before it heated up the laptop enough for it to switch off.

Transcoding operations are always CPU intensive and can cause heating problems if your fans/vents are clogged with dust. I was able to sort out a problem like this on one laptop by running a vaccuum cleaner over the air vents - no need to take the laptop apart. After that running both cores at max, the temperature dropped by about 10-15 degrees C compared to before the dust was cleaned out. Might be worth a try anyway.

---

### Post by inobe on 2011-04-11
> **alphacrucis2 said:**
>  no need to take the laptop apart. After that running both cores at max, the temperature dropped by about 10-15 degrees C compared to before the dust was cleaned out. Might be worth a try anyway.

this really depends, i have seen heatsinks caked inside and out that required a breakdown, in some laptops the owners were smokers, this was worse because the grossness was sticky:)

---

### Post by dindoliya on 2011-04-12
Thank you all for responding. I will try the vacuum as that is the only viable option. Will post back after trying.

---

### Post by dnguyen1963 on 2011-04-13
Download ArtistX distro and try K9copy from there.  I had all kinds of problem with K9copy in Ubuntu, but not in ArtistX.

---

### Post by dindoliya on 2011-04-23
alphacrucis2 and inobe, thank you for your advice. I opened the fan assembly and found that the heat vents for the sink were clogged. I used a old toothbrush to clean and then vacuumed the area. 

This issue is now resolved.

---

