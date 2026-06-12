---
title: "MythTV virgin sky cable decoder box setup  cables"
date: 2009-10-07
forum: Mythbuntu
---

### Post by davidrose on 2009-10-07
[COLOR=black][FONT=Verdana]Dear all,

I've been scouring the forums and web generally for some help to a problem set I have in mythtv/mythbuntu but I can only find piecemeal clues and I think it might be a problem facing many UK users.

Basically, I have a frontend/backend hybrid under my TV which is running mythbuntu installed on ubuntu 9.04, but instead of a normal digital signal going into the box, I have two separate TV tuners (both Hauppauge PVR 150 PCI) connected to a Virgin Media Box decoder (via coaxl) and a SKY box decoder (via composite cable yellow (video) and red-white (audio). The two decoders are still connected directly to the TV via Scart so I do not have to have the PC on when I watch TV, but only if I want to record TV (and I don't mind having the box on the channel that is being recorded since I can watch the other decoder via the other scart entry!)

So, I have set up the TV cards (set up as MPEG2 PVR ivtv), the Video sources and begin trying the Input connectors in setting up the backend. Scanning for channels, I receive about four which are basically snow. I cannot seem to get the frequency for the boxes. (I have try-all set for the frequencies, not just western Europe.)

Any ideas about where I'm going wrong?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have two ideas which may or may not be wrong (1) the decoder if connected to scart doesn’t emit a signal via coaxl? Or (2) if a decoder box is connected via composite like a video camera, mpeg2 is the wrong setting?  Help!

Thanks,

David

Hardware: AMD AThlon XP 2200, 2GB RAM, 160GB HDD, PVR150 (X2), Nvidia 5200 PCI graphic card, mythbuntu 9.04 on a ubunutu 9.04[/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]

---

### Post by gwagchunks on 2009-10-08
Hi

I'm not in front of my machine at the moment and wont be until Monday evening! I think from memory you need to setup your capture cards with the composite option (not tuner) as the tuner option is trying to get analogue bbc1/2 itv channel4 etc from the coax aerial (that's probably why you are seeing static). Composite will capture whatever is coming out of the sky box via the scart (assuming you have a scart adapter with the yellow and red/white leads in). I have my yellow red/white leads plugged into a scart adapter on the "vcr-out" of the sky box. The leads then goto the pvr-150 card (I think from memory you have the red/white audio jacks go into a 3.5mm jack in the back of the pvr-150). I also did a channel scan. This found loads of channels on composite for some reason, so I went into myth-web and edited/deleted the extra channels I didn't need from there. You can do it from myth itself, by highlighting a channel and pressing d I think. As I say it's all from memory, so hopefully someone else may be able to help in the mean-time. Hope this helps. Good luck.

---

### Post by dibuntux on 2009-10-08
Yep, I have an HVR1110, with DVB-T and analogTV. On the analog part you can choose from tuner, composite and S-video inputs. If you can, use the S-Video to get better results.

---

### Post by davidrose on 2009-10-09
Thanks to both users.  I am away for the weekend, but shall delete all my tuner cards and start again as composite.  I'll play around with the cables and see what I can generate.  I'll post any success for other users.

Thanks again,

---

