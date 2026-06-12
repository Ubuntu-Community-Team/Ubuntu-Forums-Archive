---
title: "new Nvidia 9500 GT problem"
date: 2010-03-24
forum: Mythbuntu
---

### Post by mookie60 on 2010-03-24
Mythbuntu 9.04 
pc: hp/compaq 7100
cpu: 3.6 ghz Pent4
ram: 1 gig
tuners: Happ 1600 & 150
graphics: integrated with only vga/pc video output, pci-e/x16 slot available for use


Myth has been running well.  I need to move the box to an older tv with only component and s-video inputs, so I purchased a Nvidia 9500 GT.   This looked like a good choice after viewing the Mythtv Nvidia/VDPAU page.   The card (actually an EVGA brand from Compusa) was a PCI-e and had the needed svideo output, it was also low-power relatively speaking.

For the initial test (while still connected to the current tv, a high def Sony, via the vga/PC connection), the Mythbuntu video driver no longer identified the HD capability of the TV and would only give me some form of a 4:3 display.  I verified the bios/setup was using the new card.   I tried both the 180 driver and . . . the other one, can't recall the number . . .  but when the machine rebooted it would only go into low graphics mode.

I took the card back.  In hindsight I should have spent more time trying to make it work, but I needed to have the box working.   
 
I made no attempts to setup VDPAU, but that should not matter, right?  I just wanted to know the thing was working first.  I've read some other posts that said for VDPAU I should be using one of the Nvidia drivers with this card, the 180 or the other one, so these drivers should also be working for the 9500 without VDPAU, right?

As Myth was relatively easy to setup the first time around, I haven't gained much of a grasp of all the video issues, so forgive me if I'm missing something simple.

I still need to switch this box to the older s-video/component tv, so I'd try another 9500 if I was missing something the first time around.   Or maybe another card would be more suitable, as long as its pci-e, s-video or component output, and preferably have vdpau - and not make me replace my power supply.


Thanks,
John

---

### Post by ian dobson on 2010-03-24
Hi,

Before I got a new LCD TV with HDMI input, I was using an old TV, a NVIDIA 9300 graphic card and a S-VIDEO cable. I had to go to the NVIDIA settings screen and manually setup the resolution. The maximum resolution I could get was 1024/720? I don't think you can get a higher resolution with a s-video signal.

HD recordings didn't look too bad, as the graphic card seemed to scale them down quite well.

Regards
Ian Dobson

---

### Post by mookie60 on 2010-03-24
Ian,

Yes, I should have thought to take a look at the Nvida settings app and not taken it back so quickly.  

A while ago I had an old pc with a Nvidia 6200 (agp) hooked up via s-video to a sony bravia and was able to get higher than 1280 (don't remember exactly how high, it's been a while).   Everything worked automatically with both the opensource driver and those from Nvidia.  But maybe I got lucky that time, and shouldn't expect it to always work that way.

I'm just hoping someone can tell me:  

a) a 9500 GT will work reasonably well (via the s-video to a 1080i sony rear projection tv) even if it takes a bit of fiddling - in which case I'll try again . . . or 

b) it's hit or miss, depending on motherboard, or tv, etc - in which case I still don't know which card to get. 

Thanks
John

---

