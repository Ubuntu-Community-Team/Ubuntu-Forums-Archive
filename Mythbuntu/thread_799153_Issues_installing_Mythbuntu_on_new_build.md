---
title: "Issues installing Mythbuntu on new build"
date: 2008-05-18
forum: Mythbuntu
---

### Post by johncorcoran on 2008-05-18
He there, I am a Linux newbie, but I have build quite a few windows machines in the past. I decided to build my own DVR and figured I would finally give Linux and MythTV a try.

My setup includes:
-ECS GOAL3+ AMD Sempron 3000+ 754 SiS 761 GX Micro ATX Motherboard/CPU Combo
-500 SATA 7200 Seagate Barracuda
-80 ATA 7200 Western Digital Caviar
-WINTEC 2GB (2 x 1GB) 184-Pin DDR SDRAM DDR 400
-Lite On DVD burner
-Lite on CD burner
-400 Watt PS

When I boot to the install CD and select install I keep getting the error "Kernel panic - not syncing: attempted to kill the idle task". I have read in a few other forums that this can be an issue with memory and that a common solution is to swap your sticks (flip the socket positions). I tried this with varying results, the best of which is the same error, but sometimes the machine wouldn't even start, would hang when I would try to install, and some times the install screen would be garbled and I wouldn't be able to select anything.

I tried a memory test, but it didn't to be much help, either it didn't run correctly or I didn't understand the results. Is it possible the memory is just bad or the socket on the MoBo? Both are still under the 30 day return warranty so I can send them back if I have to. Any thoughts?

---

### Post by grytpype on 2008-05-18
> **johncorcoran said:**
> I tried a memory test, but it didn't to be much help, either it didn't run correctly or I didn't understand the results. Is it possible the memory is just bad or the socket on the MoBo? Both are still under the 30 day return warranty so I can send them back if I have to. Any thoughts?

I vote for return the memory and mobo, it's not worth the trouble to debug a hardware issue when you can just get new hardware.

I'm also going to suggest getting a bigger MoBo, not a microATX, one with more SATA ports.  Your board only has two, your expansion possibilities are going to be limited.

I also don't have any info about how the SiS chipset is going to do with the large amount of data transfer MythTV needs, especially for high def.  MoBos with an nVidia chipset are known to work well, I had to return a MoBo with a VIA chipset because it couldn't handle the data.  Suggest getting a board with an nVidia chipset.

---

