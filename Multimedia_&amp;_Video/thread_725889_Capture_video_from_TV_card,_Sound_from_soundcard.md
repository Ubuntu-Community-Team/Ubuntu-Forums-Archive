---
title: "Capture video from TV card, Sound from soundcard"
date: 2008-03-16
forum: Multimedia &amp; Video
---

### Post by Ledah on 2008-03-16
Hi,

I would like to capture videos from my PS2. The composite plug is connected with the composite line-in of the TV card. The sound leads in the line-in of the soundcard. The TV card has no sound line-in.

Well, if I start the record only the video signal is captured, not the sound. I tried transcode with the parameters *-p /dev/dsp *and *-p /dev/audio*, but had no success.
I also tried mencoder and ffmpeg, but I didn't found an option to specify the sound source independently.

Any ideas, how I get it working?

---

### Post by Major_Kong on 2008-03-16
You could always do it the hard way. Rip the audio and video separately, and then mux them.

---

### Post by Ledah on 2008-03-16
I recently tried that with arecord, bur the result is horrible :D
A lot of noise and no idea how to stop it.

---

