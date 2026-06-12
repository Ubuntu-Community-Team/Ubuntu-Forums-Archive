---
title: "Jumpy / Bouncing picture with NV fx5200 tv-out through rf modulator"
date: 2006-07-25
forum: Multimedia &amp; Video
---

### Post by alamout on 2006-07-25
Hey people, any got a suggestion for the following problem:

ubuntu 6.06 with nvidia fx5200

vid card goes from s-video -> composite convertor -> rf modulator -> fairly old phillips tv which only has RF in.
Picture quality is superb (relatively) but the picture bounces up and down 2 or so centimetres constantly. I'm in Australia, so my signal should be Pal B. I've confirmed the TV actually works with the modulator by plugging in a vcr, no bounce.
Have tried replacing the TV with another (slightly newer) one with RF in, on this second tv the picture doesn't bounce but is nowhere near as clear as the old tv (weird huh).
I've tried sending resolutions anywhere between 320x240 -> 1024x768 (including the native pal res) with no change at all. I've jiggled the cables which doesn't make it any better. I've tried creating a few custom modelines to use (bit of guesswork there), none of these things seem to give any improvement. I've tried all sorts of different VertRrefresh and HorizSync settings and still no change. (tried Vert anywhere from 50-120, Horiz anywhere from 30-80).
Interestingly enough, in console mode there is no bounce, but when I start xorg it starts bouncing, from the point where the nvidia logo shows.
Last thing I am thinking of trying is trying to install windows on an old hdd to try it there, just to confirm that it could be a software/driver issue, and not just an impossibility between that particlar TV and that video card.

Any got an ideas or seen this before? I realise that I ideally would want a better TV but that's not an option right now.

---

