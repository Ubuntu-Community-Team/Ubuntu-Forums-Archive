---
title: "Hardy Nvidia 5.1 HDA AD1986A no surround??"
date: 2008-10-16
forum: Multimedia Software
---

### Post by Otown on 2008-10-16
I am a new linux user and i am trying to get 5.1 sound out of my Asus P5N-SLI onboard sound card. Nvidia HDA AD1986A. I've tried several different things to try and get 5.1 sound out of this device but have had no luck what-so-ever. I've tried creating the .asoundrc file with the fallowing 

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}

And still have had no luck getting 5.1 sound.
I have also changed /etc/pulse/daemon.conf and uncommented 

default-sample-channels = 2 
and changed it to 
default-sample-channels = 6 

and still nothing. when i open pulse audio volume control i only get front sliders. there is also no switches in the audio app to change mic or line in to center/sub or rear.  I have no idea how to get 5.1 out of Ubuntu it sucks enough my X-Fi Platinum is useless, i'd REALLY like to at least get 5.1 out of my onboard card. Any and all help or suggestions would be greatly appreciated!! 
Thanks!

---

