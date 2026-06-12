---
title: "[SOLVED] Distorted MIDI with Nvidia MCP73 sound"
date: 2008-10-26
forum: Multimedia Software
---

### Post by hansson_14 on 2008-10-26
The title above says it all:
After building a new computer with Nvidia MCP73 High Definition Audio on the mobo, I found that playing MIDI in for example Rosegarden gives a distorted sound. All other sound-ralated software and methods work: playing mp3, avi, mp4 etc in Audacious, VLC etc.
So, only MIDI is strange. I tried wiping everything by installing a fresh Ubuntu 8.04 32-bit. (I first had Ubuntu Studio 64-bit.) But it's nothing in the distro - must be something with the sound chip, Nvidia MCP73.
Also, changing things in JACK doesn't help. And I have set everything in Preferences-Sound to ALSA.

My lspci:
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)

Anybody has a clue?

/Fredrik

---

### Post by markbuntu on 2008-10-26
There is a problem with the nvidia hda chips that is solved with the 2.6.27 kernel but that was for crackly and distorted analog sound so I am not sure if it will fix your midi problem. The 2.6.27 kernel is the Intrepid kernel so of you can wait a few days for the Intrepid release you should maybe give it a try.

---

### Post by hansson_14 on 2008-10-26
Thanks a lot, I'll wait a few days!

/Fredrik

---

### Post by hansson_14 on 2008-10-31
This issue was solved after updating to 8.10, Intrepid Ibex. Seems it was that kernel-related problem mentioned above.

---

### Post by Absolom on 2008-10-31
In my case is just the opposite my sound has worked fine all the way till I installed ibex now all I get is static. The Hardware Testing program says I have intel sound.. I have a Dell Inspiron 6400 laptop.

---

### Post by jweaver28 on 2008-11-01
I'm with Absalom. The thread does not seem solved. I have a clean install of Intrepid, on a motherboard with the above onboard sound, and no sound. Nada. Since I'm a newbie, it's probably my fault, but I did download and try to install the latest Alsa drivers (issued 10/29) too. Got lots of error messages, tho no razzing sounds.

Jane.

---

