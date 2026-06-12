---
title: "Help me understand: Dual screens"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by Michael_Grosberg on 2007-10-21
I just installed 7.10 on my computer. I had 5.something installed a couple of years ago, and I remember setting up dual screens was a chore - you had to edit the xorg.conf manually. 
I love the fact that I don't have to do that anymore and that the Nvidia driver integrates well with the GUI... or so I though at first.

I quickly found the "screens and resolution" GUI in the system menu, and tried to turn on my TV-out. It worked, but then Compiz stopped working. Since I had trouble enabling both TV-out and Compiz, I posted a question in the desktop effects forum and got a reply that said to set up the screen by using "gksudo nvidia-settings". This GUI seems to replicate the same functionality of "screens and resolutions" - but after messing with both GUIs a little I noticed that they seem to be unaware of each other's settings! I can get, for example, Nvidia-settings to be set up as twinview, and "screens and resolutions" to show the second monitor is disabled. So I'd just like to know what is going on here. I assumed both are just front ends that  read and write xorg.conf but that doesn't square with the fact they can show different settings (nvidia-settings seems to hold the upper hand in a case of conflict). 

I also had weird results from using nvidia settings - compiz slowed down when I set up dual screens, so I changed the setting to twin view. the result was that the desktop still had two-screen desktop, but compiz now works faster. 

But mostly I just want to understand what is going on behind the screen - how the nuts and bolt of it works. can someone enlighten me?

---

