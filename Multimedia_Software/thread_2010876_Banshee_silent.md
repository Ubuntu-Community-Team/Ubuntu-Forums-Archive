---
title: "Banshee silent"
date: 2012-06-26
forum: Multimedia Software
---

### Post by lordbah on 2012-06-26
Suddenly Banshee is no longer making any noise. Sound settings Test Sound verifies that my speakers are still connected, and my headphones work, but banshee won't make any noise on either device. It's not muted in sound settings/applications. The play position moves along as if it was playing. ReplayGain is off, just in case that could cause this. Just a few days ago it was playing normally. There was a kernel update and I did reboot since then, I guess it's possible something got broken.

vlc plays the same tracks just fine. So I think there is no problem with the music files, the network, or the speakers. Probably the decoders are okay and pulse in general too. But I'm baffled as to what the problem could be.

Banshee 2.4.1 on Ubuntu 12.04.

Linux arctic 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by lordbah on 2012-06-27
What solved this was to turn on a Bluetooth speaker I've been using recently, connect to it, set Sound Settings / Output to it. Music began playing on that speaker. Set Sound Settings / Output back to Analog Output Built-in Audio and now those speakers began playing music. Now, I had switched output between Analog and Headphones, to no effect, and I had rebooted, so I don't get how Banshee was stuck in this Bluetooth mode. I don't get how it even knows about it, I figured it would only be pulseaudio which would know the difference. Anyway, it's working again.

---

