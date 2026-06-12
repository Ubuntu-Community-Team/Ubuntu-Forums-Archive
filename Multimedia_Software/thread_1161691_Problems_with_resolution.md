---
title: "Problems with resolution"
date: 2009-05-17
forum: Multimedia Software
---

### Post by Luca_turicci on 2009-05-17
Hi,this is my first post.

I installed ubuntu 8.04 and upgraded to 8.10 because firefox was a little slow, so, now that I run 8.10 i got a problem with resolution, in the login screen the image was like "off-center" and resolution was 900x600, and so did the Desktop. I tried a lot of different things and finaly made it "almost" work, the login screen was still off-center, but no was like in a resolution higher than 1024x768, but the desktop was perfect on 1024x768. BUT!!! when i started my PC next morning... it was again 960x600 and running displayconfig-gtk found that the 1024x768 and higher resolutions were gonne, the higher was 960x600.. again i tried many different things and finaly it returned to 1024x768 (btw, also the orange ubuntu theme changed to a grey one). But later when rebooting my pc... AGAIN!!!! 960x600 sick of it, i started lookin more, and more, i noticed that the HorizSync and VertRefresh were not in the xorg.conf...... so started looking for them... with no results, so I ran sudo displayconfig-gtk and i used the ones in there. after this, and rebooting via "ctrl-alt-backspace" i had an error message about screen, it said something about running on low resolution, reconfiguring something or troubleshooting it... i choosed reconfiguration, and using the defaul generic config... so after this the login screen is OK again, 1024x768 and CENTERED and so is desktop.

the thing is, I don't know if the next time i reboot it'll all be again the same, can anyone tell me why is this happening and how to solve it???

I have no graphic card, i use the integrated one, and my monitor is a BTC j556 bga, i don't know the exact Hsync and Vrefresh, if you need, i have a copy of the original xorg.conf and the current modified one i use.

---

### Post by Luca_turicci on 2009-05-26
well, i've seen that no one answers... so, My computer hasn't failed again, seems that it's solved...

---

