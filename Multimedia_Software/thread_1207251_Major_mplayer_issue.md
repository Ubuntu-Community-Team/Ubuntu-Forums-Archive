---
title: "Major mplayer issue"
date: 2009-07-08
forum: Multimedia Software
---

### Post by hardwarehank on 2009-07-08
After updating my packages in Intrepid, I restarted and realized that mplayer wouldn't play movies properly anymore.  I have always used the xv video out option, but now when I do that, the video and audio get all jittery and eventually the movie just pauses.

The next thing I tried was upgrading to Karmic Koala Alpha, since I like to try out the alphas way ahead of time, and I thought it might contain a more stable mplayer, which is what I thought the update might have ruined.  This didn't change anything - the same behavior is still here.

I tried killing pulseaudio, removing pulseaudio entirely, and neither of these work.  I have pulseaudio again now.

I tried changing to vo=gl and vo=gl2, both of which work slightly better, but they're just a little too slow, and when seeking I end up getting consistent pauses.

I remember a long time ago there where closed source nvidia options you could give to Xorg that would fix xv performance..

This happens with NVidia's 180, 185, and 190 closed source drivers.  Any help or suggestions would be appreciated.  I've also compiled mplayer and installed it, but it performs exactly the same way.

---

