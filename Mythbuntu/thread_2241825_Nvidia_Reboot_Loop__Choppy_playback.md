---
title: "Nvidia Reboot Loop / Choppy playback"
date: 2014-08-28
forum: Mythbuntu
---

### Post by tezcooling on 2014-08-28
I have a pretty stable Mythbuntu 12.04 setup been running fine for several years. 

I was using the inbuilt intel graphics card with a DVI to HDMI adapter.

To tidy things up I installed a Nvidia GeForce 610 to make everything a bit neater.

The nouveau drivers worked fine, when I tried to install the nvidia drivers the machine just got stuck in a reboot loop, the only way I could fix it was to boot to command prompt, purge the Nvidia drivers and then let nouveau re install on the next boot. I've tried nomodeset, several different drivers, every time just ends in a reboot loop.

The only problem I have with the nouveau drivers is when I watch a program recorded from a non HD channel its very choppy. If I play the same recording with VLC, or if I transcode it to 1080p resolution, it's fine. 

Anyone any idea on where I go to either get the Nvidia drivers working or sort out the playback issue?

Thanks

---

### Post by uteck on 2014-08-29
So the frontend is running at 1080 and if you try to wtach anything not in 1080 it is choppy?  Do shows at 720 play fine?  Do you have the playback settings set to scale video to the display resolution? Check if Video Aspect Override is enabled.

---

### Post by tezcooling on 2014-08-30
Thanks for the help.

I checked a few more programs. 720 seems to play okay, but anything lower than that and it becomes choppy. 

I just disabled aspect ratio override and zoom and it seems to have fixed it! I'm just recording some SD programs to make sure.

I played with the Nividia drivers all day yesterday and still get stuck in the reboot loop - the Nvidia Module never seems to get loaded and for some reason as soon as X tries to start it causes the PC to reboot. But hey guess I don't need the drivers if the playback is okay now!

---

### Post by tezcooling on 2014-08-30
Yup perfectly smooth playback thank you!!!!!!

---

