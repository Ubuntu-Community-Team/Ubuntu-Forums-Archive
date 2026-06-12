---
title: "Radeon 9200 TV-out black and white"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by sanmadjack on 2007-10-28
I'm setting up a media center PC using gutsy, but I'm running into a rather serious problem. As long as I have only the tv connected via my S-Video to composite cable, the computer uses it. The picture however is in black and white. When I had a regular monitor attached, I was able to use the ati driver but now it fails and starts up in low-graphics mode . I have only been able to get the vesa driver to work. I tried installing the proprietary ATI drivers via Envy but it said I needed legacy drivers and that they are not supported by my current OS. The card in question is a Radeon 9200. I'm a little out of options, as I doubt I will be able to get TV-out working properly without any drivers.

---

### Post by steve0921 on 2007-10-28
I can get you a baby step closer to a working system. I too have a radeon 9200 and have got tv out working with the proper "ati" open source driver (instead of vesa). Check out [this thread]("http://ubuntuforums.org/showthread.php?p=3597291") for more info. Their approach uses the new and fancy xrandr and I especially found BungaMan's xorg.conf useful.

However, I too do not have colour. I've tested the S_video to composite cable on another computer, and it appears to work. If you sort out your problem, I'd like to know how you managed it.

---

### Post by sanmadjack on 2007-10-29
Okay I am now to the driver-working-but-tv-out-is-still-black-and-white stage. I've been reading around and I'm thinking it might be a component vs. composite thing. I've read on several forums to try setting the output to S-Video or composite, but no one seemed to think it'd be a good idea to tell us how to do that. In addition, I am unable to use 3d or video acceleration on the TV. All I get is black videos and a really low framerate glxgears (is not a benchmark, I know).

---

