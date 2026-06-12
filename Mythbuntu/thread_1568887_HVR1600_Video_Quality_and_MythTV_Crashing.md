---
title: "HVR1600 Video Quality and MythTV Crashing"
date: 2010-09-06
forum: Mythbuntu
---

### Post by Chromag on 2010-09-06
First off, I'm new to MthTV and Mythbuntu.  I installed 10.04 on my machine with a GeForce 210 video card connected via HDMI and an HVR1600 connected to antenna via ATSC.  I set up the 1600 via the wiki instructions.  It scanned my channels and found what I was able to receive.

The first time I clicked on "Live TV" I got the "Please wait" screen, a black screen with the program data of one of the channels, then it immediately dumped out to the X-windows screen - so I'm guessing the frontend crashed.  

After trying a couple times it would lock on and work.  But when it does work it appears as though I'm seeing the interlacing or something odd.  During quick movement I'm seeing lines.  If someone onscreen makes a quick movement or a car drives by quickly I get a terrible line-type artifact happening.

Any ideas what's causing the lines and/or the crashing?

Thanks.

---

### Post by tmcgary on 2010-09-06
Chromag,

I have this card as well, however I am using it for clear-qam reception. It can be quite a problem card if you have read many forum entries.

Have you tried an in-line signal amplifier? This resolved alot of problems for me. I am using one from radioshack. If it didn't work for you, you could just return it. Best of luck!

---

### Post by JMcFly on 2010-09-06
Start the backend and frontend in terminal and try again, sometimes it sees the 1600 as a multiplex capable card while it is not and you'll see an error about multiplex.

---

