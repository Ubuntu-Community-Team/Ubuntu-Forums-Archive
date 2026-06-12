---
title: "Sound Blaster Live Audigy sound issue"
date: 2007-03-17
forum: Multimedia &amp; Video
---

### Post by mmilitia9 on 2007-03-17
I have a Sound Blaster Live Audigy 2 ZS sound card and It works with Ubuntu and everything... But the sound doesn't come out of my 5.1.  Only 2.1 comes out I believe.

When I went to System, Prefs, Sounds, Sounds tab.. the default card is the Audigy 2 ZS.  
What other options should I check to get it configured properly?

Thanks


Dominick

---

### Post by DoorGunner on 2007-03-18
Create this file

sudo gedit ~/.asoundrc

Enter the following into it and save it.

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}


reboot your system and you should now have 5.1 surround:)

---

