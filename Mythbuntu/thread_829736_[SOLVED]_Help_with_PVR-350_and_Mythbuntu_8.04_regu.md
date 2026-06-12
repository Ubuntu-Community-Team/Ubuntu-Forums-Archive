---
title: "[SOLVED] Help with PVR-350 and Mythbuntu 8.04 regular setup"
date: 2008-06-15
forum: Mythbuntu
---

### Post by jjlllk on 2008-06-15
I have been troubling myself with this for weeks now, and can't be able to set this up correctly.
I have a Antec Fusion Black (havent even startet to get the knob and lirc ready, but don't see that as my first priority)
Gigabyte MA 780G D-S2H
PVR-350 the one with tv-out (which is what I want since I am still waiting to get a full HD 32" Tv when it will become affordable).
 
TV (PAL) setup to the PVR-350 tv-out
I live in Germany therefore got myself an account at EU_EPG_DATA which as far as I can tell works (downladed for 2 weeks a lot of data)

In the MythSetup I chose the PVR-MPEG Encoder card driver not the V4L. I scan for channels and find them (cable Deutschland setup) after a second try the channels are linked to the xmltv data.
But when I run the frontend (which is running on my LCD on the VGA-Port) and start Live-TV. The TV gets on, the OSD gives me the needed infos, the Menu (m) is working and can be read clearly but I only see fuzzy white snowstorm image. On all channels.

I tried Cat output of videos (cat XX > /dev/video16) and it seems to have a high alpha of the fb (black box over the image) 

Can anyone help me on this, feel free to hit some questions at me. Should I do a complete reinstall ???

---

### Post by jjlllk on 2008-06-15
O.K. I finally got it to work
All I had to do, and it probably got messed up in the installation process, was to set the Channels (E5-E19, SE5-SE20, S21-S35 or I could have set the Mhz (not sure on that though)) in the Backend-Setup to each channel. It wasn't enough that the xmltv data was correctly lined up to the channels.

Glad If I could help, now on to the next project....X on TV-OUT (keep my fingers crossed, be back if I need help :) )

---

