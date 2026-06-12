---
title: "No sound mythtv frontend. Mythbuntu desktop os has sound"
date: 2013-12-10
forum: Mythbuntu
---

### Post by sebbie2 on 2013-12-10
I am new to mythbunu and mythtv. I usually use IVTV with my PVR-150.

I decided to try Mythtv.  I did a fresh install of Mythbuntu from the ISO I downloaded from the offical site.

After a ton of guess and try, I was able to get mythtv to display video from my Comcast Cable Box however I have no sound. 
I have tried every option under AUDIO in Mythtv. Most just send static over my speakers and a few send nothing.

However, Linux its self plays audio just fine. I can play via VLC and the video file has sound.

I have tried looking at ALSA -L however, not sure what to do as it lists 15 options.  My video card has HDMI output, however I am not using it.

I have an Onboard ALC892. 

I can send more info, if someone can tell me where / how to find it.

---

### Post by sebbie2 on 2013-12-10
I was able to resolve this by setting Mythtv to my base sound card ASLA: SB: ALC892 Analog
Saving and then rebooting.
Now I have sound.
Sorry and Thanks.

---

