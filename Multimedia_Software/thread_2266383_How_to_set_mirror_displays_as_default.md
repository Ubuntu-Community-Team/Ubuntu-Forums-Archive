---
title: "How to set mirror displays as default?"
date: 2015-02-22
forum: Multimedia Software
---

### Post by jim_deadlock on 2015-02-22
I have my computer hooked up to a normal display and also my TV via a HDMI cable (for watching Netflix). It all works nicely. However, every time I start my computer I have to reset the display configuration to mirror/clone but I would like to set mirror as default. I normally switch it using the standard display settings (screenshot below), or I can also set 'clones' via the NVIDIA controls, with the same result (screenshot below). However, my problem is that whenever I reboot the computer I have to go thorough this resetting every time, there seems to be no way to save mirror/clone as default. I've tried 'save to X configuration file' on the NVIDIA panel but that seems to have no effect. I've also tried running a script at startup with a command to update the display, this works initially but then my display hangs soon after and I'm forced to reboot so that's no good. I suspect that I need to do something so that my xorg.conf is detected at startup, but I'm not sure what. Any suggestions?

[IMG]http://i932.photobucket.com/albums/ad168/jim_deadlock/screendisplay.png[/IMG]

[IMG]http://i932.photobucket.com/albums/ad168/jim_deadlock/nvidia.png[/IMG]

---

### Post by Bucky Ball on 2015-02-22
*Thread moved to **Multimedia**.*

I use arandr for my monitor set up and that seems to stick on reboot just fine. It is in the repos (Software Centre). You will then find it in the Settings menu (might be diff on Ubuntu, I am using a mini install with xfce4 desktop environment). 

Hope that helps. ;)

---

### Post by jim_deadlock on 2015-02-22
So I've created a script using arandr and then added that script to startup apps (is this the correct method?) and it seems to be working nicely so far. This is what I did before with the startup script when it kept hanging but I did the randr script myself, so I'm thinking maybe I just didn't do a proper job with the script before. Anyway thanks, seems to have done the trick.

---

