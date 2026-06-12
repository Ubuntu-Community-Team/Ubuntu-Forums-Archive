---
title: "Flash Audio is disfunctional only after using a sound program."
date: 2009-12-29
forum: Multimedia Software
---

### Post by secondstage on 2009-12-29
If I immediately open Firefox and go to youtube then the audio works great, and the video will load. But if I try to watch a youtube video after playing music through Rhythmbox, then the video will stop at 1 second, without loading a picture, and without putting out any sound. Also note that I am using the optical out on my motherboard to get the audio to my reciever. Do I need to reinstall the flash plugin to let it reconfigure itself for the optical out, or is there some other thing I need to do?

---

### Post by secondstage on 2009-12-29
Upon a bit of inspection with Pulseaudio Volume Control, it appears that the Flash audio is being routed out the analog output (not the optical out). Also in Pulseaudio Volume Control, there isn't the digital out (aka optical out) sink for audio devices. 


So how can this be fixed?

Dumb me. Just reboot. This allows for Pulseaudio etc to adjust itself. (This thread helped too [http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506))

---

