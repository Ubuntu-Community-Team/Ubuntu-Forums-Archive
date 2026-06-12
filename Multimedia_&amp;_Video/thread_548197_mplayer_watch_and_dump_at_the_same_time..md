---
title: "mplayer watch and dump at the same time."
date: 2007-09-11
forum: Multimedia &amp; Video
---

### Post by OmnipotentEntity on 2007-09-11
Question, I'm looking into making my computer into a place where I can record myself playing video games.  Like PS2 games.

I have my capture card installed and configured and I can play it with mplayer or anything else really.

However, I can't play it and capture it at the same time.

Well, I've come up with two different ways to do that actually, but each has a problem.

I can tee /dev/video0 to two fifos and play from one and record from the other, but it only runs at 10fps because the v4l driver doesn't run the control commands for the device correctly because it's attempting to act upon the fifo and not the block device.

Or I can mplayer then dump the video stream to a fifo, tee the fifo into another instance of mplayer and mencoder, but that's results in a 1/5 second of lag, which is undoable for playing video games.

Does anyone know how I can send the device control signals directly to /dev/video0 so when I attempt to play the video it runs at 29.97 fps?

Or of a different way to do it altogether?

---

