---
title: "ac3 audio + mythbuntu"
date: 2010-08-11
forum: Mythbuntu
---

### Post by russell5 on 2010-08-11
So my problem is i have a lot of movies encoded with ac3 audio. I currently have 4 speak system plugged into my mythtv box. I get sound from all speakers. 
But when i play a ac3 encoded movie the volume is really low. i turn it up all the way still hard to hear. 
So i did some searching and i found a command for mplayer that fixes it. 

I tested and sounds good. 
its mplayer -af volnorm 2:0.25 

does anyone know how to fix this in mythtv internal player or should i jsut change form internal to mplayer with the command?

---

### Post by LowSky on 2010-08-12
go through the general settings on MYthTV frontend. by default myth has sound at 70%, just up it to 100.

---

### Post by russell5 on 2010-08-12
i did that. also made sure alsa mixer was up all the way. I think i am going to have to use mplayer as default player and use the -af volnorm swicth

---

