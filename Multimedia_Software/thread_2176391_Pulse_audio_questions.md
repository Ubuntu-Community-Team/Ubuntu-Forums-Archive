---
title: "Pulse audio questions"
date: 2013-09-24
forum: Multimedia Software
---

### Post by dan9550 on 2013-09-24
So i have installed in my system an ASUS Essence STX, i was wondering if it would be possible to connect a line in source to the aux in on the card (which is a header on the card itself) then have the input from the aux in playback on my system with loopback. When i open and Pulse Audio Control Panel and look under Input Devices, i see one input for the card and i can select from Mic, Line, and Aux is it possible to use the Aux input and Mic at the same time? If so how?

---

### Post by lidex on 2013-09-29
Perhaps alsamixer can help. Run it in a terminal with the alsamixer command. Hit F4 for capture devices.
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

