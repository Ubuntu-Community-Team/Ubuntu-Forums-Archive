---
title: "NVIDIA card how-to"
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by Astronomerob on 2008-02-06
Hello everyone,

I just managed to (finally) get my NVIDIA GeForce 8500 GT card working in my Gutsy installation.

I'm submitting this post so that others may benefit from my luck in figuring out my problem. I hope that this is okay with everyone here.

My motherboard has a built-in (onboard) 6150SE video card and the xserver was always defaulting to it. I'd tried using the "lspci" command to find the BusID for the card, but it always came up in an unacceptable format and I couldn't figure out how to get it right.

I worked around my computer illiteracy by typing in "nvidia-settings" and clicked on the 8500 GT that showed up in the side bar and BAM! there was the Bus ID in the proper format. So I loaded up the xserver reconfigurer with "dpkg-reconfigure xserver-xorg" and left everything as default except the driver (which I set to nvidia) and the pci Bus ID.

Ubuntu is awesome!

---

### Post by Existentialist on 2008-02-07
I have found that disabling on-board video and sound also works.  When Ubuntu doesn't see the integrated option it will default to the sound/video card in my experience.  Of course this doesn't work on all motherboards, but when it does it doesn't hurt to have it off if you aren't using it anyways.

---

### Post by bwtranch on 2008-02-07
Glad you got it working. Don't be too cocky though. You were just lucky.

---

### Post by Astronomerob on 2008-02-07
Oh! You don't need to tell me! I'm well aware of how lucky I was that that was all that was wrong!:)

---

