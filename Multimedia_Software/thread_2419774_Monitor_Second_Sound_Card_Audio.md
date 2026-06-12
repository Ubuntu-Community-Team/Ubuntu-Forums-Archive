---
title: "Monitor Second Sound Card Audio"
date: 2019-05-25
forum: Multimedia Software
---

### Post by kf6sgy on 2019-05-25
I am using a USB sound card in my laptop to send and receive audio to my ham radio. The last piece that I have been unable to get working is the ability to monitor the line in audio from the USB sound card using the laptop's speakers.

I have been reading up on this and all the potential solutions I found said to load the loopback module for PulseAudio. When I would load the loopback module, in pavucontrol under the Recording tab would only show "Loopback to Audio Adapter (Unitek Y-247A) Analog Stereo from" and list the built in audio and the Unitek audio adapter. When I unplug the Unitek card, the Recording tab goes back to allowing monitoring of it's own audio. I seem to be unable to figure out how to get the on board sound card to monitor the USB sound card.

My audio configuration is the stock Xubuntu except for the addition of the USB sound card which required no configuration by me. Does anything in /etc/puls/default.pa need to be added or modified to flip the behavior of the loopback module when both cards are operational?

---

### Post by kf6sgy on 2019-05-26
Nevermind, figured it out on my own.

---

### Post by wildmanne39 on 2019-05-26
Glad you fixed it, please post your solution so others may benefit from your answer.

Thanks!

---

