---
title: "Choppy HD live tv"
date: 2011-04-10
forum: Mythbuntu
---

### Post by rudy1094 on 2011-04-10
When I watch live high definition tv the video is fairly choppy. From several previous posts it seems that HD tv requires a lot of CPU usage. How do I determine if that's the cause or it its my tuner card,  video card etc.?

I was initially using a dell dimension 2350, but I then installed things on the a Dell Optiplex GX520 to see if the problem went away with the faster computer. It got better with the GX520, but still not great. The GX520 has an Intel Pentium D 2.66GHz processor. My tuner card is a DIVCO Fusion HDTV 5 RT Gold and my video card is a Geforce 6200. I only have 1GB of RAM. Would additional RAM help? I'm considering upgrading both the video card and the tuner card, but I haven't figured out what the most appropriate replacements would be.

---

### Post by uteck on 2011-04-11
HD video, especially x.264 needs lots of power that older CPUs and video cards can't handle, RAM has nothing to do with it.

I don't think the 6200 card will work with VDPAU, but I know the 8400 does.  I have a fan-less 8400 in my Atom system and it plays back HD video fine, and makes no extra noise.
So I would recommend you try a new video card and change your playback settings to use VDPAU so the video decoding is offloaded to the video card.

---

