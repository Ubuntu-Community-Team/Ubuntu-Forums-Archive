---
title: "No center channel on HD material."
date: 2009-04-17
forum: Mythbuntu
---

### Post by AKADAP on 2009-04-17
I know all speakers are connected correctly and work because the test pattern outputs a tone on each speaker. (well, I know I did once, can't seem to find the tool I used then though, so I can't test it again).

Anyway, I get sound out of the center speaker when playing recorded standard definition stuff, but when I play HD stuff, I only get the background sounds. The characters on the screen are talking, but I don't hear them, just background music & sound effects.

I am using the analog out as I have never been able to get the digital outputs of this motherboard (asus P6T Delux) working. I read somewhere that this is a bug that will be fixed in the next version of the kernel.

I have been working around this problem by using the upnp to my PS3. (PS3 gets a much better picture (no tearing, and no feathering), but occasionally it crashes, sometimes it has lip-sync issues (fixed by re-winding a bit), but sometimes it just won't play a file).

---

### Post by AKADAP on 2009-04-18
Given the lack of response, I decided to try Edisonian research on the options available in the MythTV setup.

I hate doing this because there is a high probability of screwing something up much worse. In a way that a newbe like me doesn't know how to undo. Last time I messed with the audio on MythTV, I was stuck with no sound at all until I re-installed Ubuntu completely.

This time I had much better luck.

I changed "Audio output device" from "ALSA:Default" to "ALSA:surrount51".
Now I have all channels. Volume is a good 10 dB lower than other sounds on the system, but at least I can now watch the recordings.

---

