---
title: "play .ogg video frame by frame"
date: 2009-12-23
forum: Multimedia Software
---

### Post by eotakos on 2009-12-23
hello!

i have an "xgraph" program that plays videos of graphs from data files. The thing is that for my data it runs pretty fast and i can't see what's happening. The whole idea was to use gtk-recordmydesktop to record the video, and then play it as slowly as i wanted in avidemux.

unfortunately avidemux won't open the .ogg files (either generally or especially from recordmydesktop - i don't know).

so, any ideas on how to see such a file frame by frame would be highly appreciated

thanks in advance

---

### Post by andrew.46 on 2009-12-23
Hi eotakos,

MPlayer will play *forward* frame by frame with the use of the default '.' key, but as far as I know will not play *backwards* in the same way. Perhaps this might be what you are afte?

Andrew

---

### Post by eotakos on 2009-12-24
thank you very much! i already had mplayer installed but i didn't know this trick with the '.' key.

in the meantime i've converted every single animation to .avi using ffmpeg (quite painfull i might say) in order to use avidemux and play the files frame by frame

thanks for the advice, very helpful indeed. I certainly will use this in the future!

---

