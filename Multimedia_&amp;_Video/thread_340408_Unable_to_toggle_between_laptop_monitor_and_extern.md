---
title: "Unable to toggle between laptop monitor and external monitor"
date: 2007-01-17
forum: Multimedia &amp; Video
---

### Post by ked on 2007-01-17
I've got an Acer Travelmate laptop with a GeForce Go 6600 video card. I'm not able to toggle between the laptop screen and any external device (monitor or video overhead) by using Fn+F5 keystroke. This action just freezes my laptop and I have to reboot. However, if I boot the laptop with the external monitor connected, it chooses the external monitor by default. Has this got to do with dual monitor configuration of X? Any help to get this to work is very appreciated...

Cheers,
Ked

---

### Post by lhtown on 2007-01-18
I am guessing that the two "monitors" aren't the same resolution and that maybe it is trying to apply the original settings to the second whereupon it fails. It isn't exactly the same to have dual monitors as it is to have alternate monitors.

I have a Travelmate 290 and it works on it when I switch to my digital projector and back, but it has the same resolution as the computer screen

---

### Post by ked on 2007-01-19
I see. Do I need to install additional software before setting up X for dual monitors?

Ked

---

### Post by lhtown on 2007-01-19
Don't get me wrong, it should work even if your displays are different resolutions although it might not fill the screen on the larger one.

I just noticed you said you had an Nvidia card. You might try disabling the Nvidia driver (assuming you did install it and it is working) to see if it works. 

Also, you might set X to a lower resolution and see if it works like that to try to diagnose the problem. After you actually find out for sure what it is choking on, then you can go about looking for solutions.

I have never had to reconfigure X to get mine to work, but you may have to. If you search around about switching monitors, you might come up with something. It isn't that uncommon, and I think maybe I remember reading about a similar problem a while back on these forums.

---

