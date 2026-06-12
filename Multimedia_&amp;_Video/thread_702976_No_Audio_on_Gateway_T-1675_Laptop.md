---
title: "No Audio on Gateway T-1675 Laptop"
date: 2008-02-20
forum: Multimedia &amp; Video
---

### Post by tomsa on 2008-02-20
I just installed gutsy last night on my new Gateway T-1625 Laptop, and everything seems to be going swimmingly.  I have 3D Graphics going and everything.  I just have no sound, and don't know where to begin to fix it.  When I run lshw, I get this (what I think is pertinent only):

*-multimedia
                description: Audio device
                product: Radeon X1200 Series Audio Controller
                vendor: ATI Technologies Inc
                physical id: 5.2
                bus info: pci@0000:01:05.2
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=HDA Intel latency=64 module=snd_hda_intel

And

 *-multimedia UNCLAIMED
             description: Audio device
             product: SBx00 Azalia
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=64


    Now, I have tried alsamixer to see if I needed to unmute things, and it didn't seem to have  any effect.  When I try playing a test tone using the sound preferences menu, the window locks.  The thing that sticks out to me most is that bit about "*-multimedia UNCLAIMED"  but I just don't know how to fix it.  Can any of you please help? (sorry if this belongs in the beginner section)

---

