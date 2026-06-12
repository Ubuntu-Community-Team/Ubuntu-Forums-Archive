---
title: "totem / rhythmbox silent mp3 playback - gstreamer works"
date: 2009-10-20
forum: Multimedia Software
---

### Post by your_zero on 2009-10-20
I'm having an issue with mp3 playback in both Totem and Rhythmbox. They'll play the mp3 with no errors, but there is no sound. FLAC playback is fine in both. 

I thought it was an issue with gstreamer, but direct playback with gstreamer works:

gst-launch-0.10 playbin uri="file:///home/josh/Music/mp3/oldies/beatles-birthday.mp3"


I had two sound cards. I currently have one disabled via modprobe in trying to fix this issue. I've tried reinstalling Totem and Rhythmbox.

Any ideas?

---

