---
title: "Dual screens, Compiz-Fusion and Xserver-XGL"
date: 2007-11-19
forum: Multimedia &amp; Video
---

### Post by foof on 2007-11-19
Hi!

I have Kubuntu 7.10 installed on my computer with Compiz-Fusion activated with my NVidia 6200 card.

I wanted to use my S-Video output to a TV, but I only got so far so I could get a cross cursor with a black screen on my TV. Another problem I got was that I couldn't get nvidia-settings to accept that I really was using the proprietary nVidia driver. I finally solved all this by removing xserver-xgl from my system! 
> sudo apt-get remove xserver-xgl

This solved two problems I got. First I could start nvidia-settings and configure it to a dual screen setup and one thing that way annoying me before was that I didn't had the option to turn my computer off when logging out, there where only one option and that was log out! Now I have all options again! :)

So now I have all the benefits of Compiz-Fusion on my main screen and if I move my cursor down under the bottom of my screen, it slides into my TV-screen and I can start a movie there or whatever I want.

So what is xserver-xgl good for?

Now it's just one more problem... I don't get any colors on my tv!
Is it a setting in my computer/nvidia or is it my TV? I got a 29" LCD-TV from DiBoss.

One more thing I have to figure out is how to get the tv-out displaying a HDTV picture in 720p. Someone who knows??

---

