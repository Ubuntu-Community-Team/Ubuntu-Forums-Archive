---
title: "XviD decoding... flickering and bad frame rate"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by dodgePT on 2007-05-28
Hi all, first i wanted to thank this marvellous community for all the support and great knowledge provided.

I changed 100% to ubuntu, and future seems brighter now that i finally escaped MS claws.
Despite all the problems that feisty threw in to me, i've been able to solve them all thanks also to you all.
But one thing stills bugs me: video decoding.
XviD decoding as made me spend hours searching and researching, but unfortunetelly I keep getting some strange flickering in XviD/DivX video, as well as poor frame rate no matter what video output method I select in any of the available players. Scan lines are visible when I drag the player window, as if my PIV 3.0Ghz didn't have enough horse power to handle it. Also i think that there's too much gama (image too bright).

A screenshot wouldn't help in this case, but it seems that the fields in the frame that change during XviD decoding are constantly flickering, and overall image quality is kind of blurry. I know we're talking about a lossy codec and i can't escape from some quality loss, but I tested those same videos in my wife's computer running XP, and quality is completelly different, for better that is. Also, all videos I tested were DVD-rips and some of them with high bitrates and great A/V quality.
Post processing also doesn't help.

Some specs for my system:
CPU: PIV 3.0Ghz
Memory: 1GB DDR
GPU: ATI 9600 PRO 256MB


I'm using open source drivers, with beryl running flawlessly through AIGLX. Turning off beryl and desktop effects also doesn't help.

Strange thing is, i don't see anybody complaining about this. Am i doing something wrong, or is it something to do with the combination of codecs installed?

I followed the tutorial in the sticky thread in this forum in order to enable multimedia for my ubuntu, but this problem is still getting on my nerves.
Should i change to proprietary drivers? Download and install xvattr and play with it's options?

Please share some knowledge on this one, because i'm all out of ideas.
Thanks in advance ;)

ps. the flickering is mainly noticeable in more-or-less-one-colored areas and it seems to be related with B-frames decoding.

---

### Post by tonti on 2007-06-05
you and me brother! videos are too bright on my acer laptop! i'm now considering switching back to xp :s weird thing is it works well on my desktop pc

---

### Post by dodgePT on 2007-06-05
> weird thing is it works well on my desktop pc

That's why i say that it must be some sort of combination of codecs, device drivers and hardware configuration.

I uninstalled/reinstalled all codecs, and now its even worse. Wether i choose X11 or Xshm, i have different problems. In one case, i get good framerate but pixelized fullscreen image. If i start mplayer with 'zoom' option, image isn't pixelated anymore, but i get bad framerate. That flickering i mentioned earlier seemed to dissapear.

I tried xvattr, and played a bit with it, managed to reduce some gamma, but the other problems persist...

---

