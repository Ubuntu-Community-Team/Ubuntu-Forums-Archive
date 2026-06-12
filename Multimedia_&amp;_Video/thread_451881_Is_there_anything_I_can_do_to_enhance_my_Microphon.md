---
title: "Is there anything I can do to enhance my Microphone with Skype?"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by mmilitia9 on 2007-05-22
Hi, I'm currently on Ubuntu 7.04 with a Sound Blaster Audigy 2 ZS...

I was curious if the sound card has been installed properly because I get poor quality with my logitech microphone.  People can somewhat hear me, but not really.  I've tried the Mic Boost, but I don't like the fact that I get to hear myself talk through the headset with it enabled. 

Is there anything I can do about this?


Thanks,

Dominick

---

### Post by BitTorrentBuddha on 2007-05-22
If it's plugged into a USB port it is treated as its own sound device which you must manipulate separately by changing device in the volume control app. It took me a long time to figure that out on my mic, and I hope your problem is so easily fixed as well.

---

### Post by mmilitia9 on 2007-05-22
Nope.. It's plugged right into the sound card.  I seem to hear a lot of background static as well while on a call.  Any ideas?  This crap doesn't happen on WIN so it's def something related to a sound issue on Ubuntu somehow.. hmm.. Maybe it's skype?  haha.. Who knows.

Dominick

---

### Post by BitTorrentBuddha on 2007-05-22
Have you dropped down into alsamixer to check and make sure all non muted volume knobs are at their highest? (Excluding the master volume presumably.) ```
alsamixer
```If that doesn't fix it and the hardware works on windows, then it's a problem with the drivers available. Sorry I can't be of more help.

---

### Post by samuliri on 2007-05-23
Check this:

[http://ubuntuforums.org/showthread.php?t=143512](http://ubuntuforums.org/showthread.php?t=143512)

---

