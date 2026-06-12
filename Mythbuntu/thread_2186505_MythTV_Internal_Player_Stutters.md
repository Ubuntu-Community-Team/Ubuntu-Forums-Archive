---
title: "MythTV Internal Player Stutters"
date: 2013-11-07
forum: Mythbuntu
---

### Post by clayclai2 on 2013-11-07
My system is an AMD Alhlon 64  running on a GA-K8NF-9 MB with Nvidia G10 video and lots of SATA & IDE disk space. Running Ubuntu 12.04 and MythTV 0.27

At some point my Internal mythplayer developed a terrrible audio stutter. and I found the usual troubling messages in my /var/log/mythtv/mythfrontend.

[INDENT]Oct  9 12:33:45 server mythfrontend[3275]: E CoreContext audio/audiooutputalsa.cpp:211 (SetPreallocBufferSize) ALSA: Error opening /proc/aso
und/card2/pcm9p/sub0/prealloc: Permission denied. 
Oct  9 12:33:45 server mythfrontend[3275]: E CoreContext audio/audiooutputalsa.cpp:213 (SetPreallocBufferSize) ALSA: Try to manually increase audio buffer with: echo 128 | sudo tee /proc/asound/card2/pcm9p/sub0/prealloc
Oct  9 12:33:45 server mythfrontend[3275]: E CoreContext audio/audiooutputalsa.cpp:545 (OpenDevice) ALSA: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
[/INDENT]
and lots of [INDENT]Oct  9 16:33:25 server mythfrontend[3275]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(5): Waited 102ms for video buffers AAAAAAAAAAAAAAAAAAAUUUUUuUUUUuLP
[/INDENT]

In my case the stutter was accross the board, TV, videos, streaming, SD, HD, it didn't matter. They all stuttered. But the same files played find with mplayer, gxine and vlc, go figure.
It started with mythtv 0.25 so I did an upgrade to 0.27. The upgrade went perfectly. Everything was preserved, including the stutter!
I changed video card, other hardware, forced drivers not to load, removed pulseaudio. Nothing got rid of the stutter. It was driving me nuts!

Finally I solved it. It was simply a permission error in /home/mythtv which was not owned by mythtv! 
How this happened is another matter. I run mythtv as another user but somehow the wrong ownership of /home/mythtv caused the audio stutter with the internal player.

I have written this up because nowhere in my travels did I find this mentioned as a possible problem and if you are reading this it may be yours, so check the permissions on /home/mythtv and save yourself days of searching.

---

