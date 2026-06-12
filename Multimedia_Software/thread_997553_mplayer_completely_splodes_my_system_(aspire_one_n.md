---
title: "mplayer completely splodes my system (aspire one netbook)"
date: 2008-11-29
forum: Multimedia Software
---

### Post by BetterSense on 2008-11-29
I have an Acer Aspire One netbook and running Hardy Heron. Attempting to play a video, any video, with mplayer turns the screen blue and completely crashes the system. I'm unable to even use ctrl+alt+backspace and have to remove the battery.

Disabling compiz first results in only the xserver exploding, at least then I can reset xserver.

Strangely, the tab-complete function does not work with mplayer, as if it doesn't recognize the video files as such. 

VLC, xine and totem also fail to play any video. 

Any idea where I could start?

---

### Post by BetterSense on 2008-11-29
On a hunch and an extreme distrust of pulseaudio I tried using ```
mplayer -ao alsa *
``` and that lets me actually play some videos now. Although the tab-completion thing is still puzzling me.

---

