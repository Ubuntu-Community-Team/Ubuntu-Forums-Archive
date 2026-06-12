---
title: "VLC freezes at end of .mpeg4 &amp; .mov file"
date: 2008-06-05
forum: Multimedia Software
---

### Post by Frogbarf on 2008-06-05
A friend prepared a video on his Mac in .mov format, and converted it to mpeg4 format as well. When I play _either_ of these with VLC, after the video finishes, VLC locks up. It's still in play mode but the screen is plain white and VLC is completely unresponsive: neither menus or pause work.

If I force a quit, I can then run VLC again.

I'm using 7.04 (Feisty) just updated yesterday.

Anybody have any idea what is happening and how to fix it?

PS: if you suggest a cure or ask for more information, please be absolutely explicit about what I have to do. My command of Ubuntu-geek-speak is very poor, and I am often unable to make sense of overly telegraphic instructions in these forums. Don't assume I know where _[COLOR="Red"]any[/COLOR]_ file is, for example! TIA

---

### Post by cariboo on 2008-06-05
Does this happen with any other video files or just this particular one? More info would be helpful.

JIm

---

### Post by Frogbarf on 2008-06-05
Good point, Cariboo97, and I should have thought of checking before posting in the first place. Mea culpa.

I've now tried it out with a .divx file and a .wmv file, and the same behavior occurs. (These are not versions of the same file as the .mov and .mpeg4.)

While VLC was frozen I went into the system monitor and looked at the list of processes. WVLC was listed as "sleeping".

Furthermore, when I switched back to the VLC window, it didn't paint the screen: just the surrounding frame, which is probably painted by Gnome or X.

And when the .wmv file finished, it stalled on the very last video frame, not the white screen the other three formats gave me. Possibly they have a blank video frame at the very end?

To use non-geek-speak, it seems like VLC goes to sleep at the end of the video and nothing can awaken it.

It's quite possible that there's some setting or other in VLC that causes this, but if so, I have no idea what it might be, nor where to go to change it.

Is there anything else I can do to provide diagnostic info?

---

