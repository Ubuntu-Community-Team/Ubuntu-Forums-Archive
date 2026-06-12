---
title: "Watch TV  doesn't work - Can't schedule recordings"
date: 2009-06-29
forum: Mythbuntu
---

### Post by jeli2657 on 2009-06-29
I installed Mythbuntu 9.04 with a Hauppauge HVR-1600.  I followed this guide:
[http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)
My firmware and driver output matched what was displayed, so I did not follow the instructions to update them.  I can scan channels and get my guide, but when I try to watch live tv, the screen flashes black for a few seconds, then takes me back to the MythTV interface.

When I try to go to the guide and schedule a recording, I click save settings, but nothing stores in my scheduled recordings, and nothing is done.

After this happened, I followed the instructions in the link above to download and compile drivers for the card, but that did not have any effect.  I tried recording on both an analog and a digital channel, but neither work.

Any ideas?

---

### Post by mookie60 on 2009-07-02
I'm running 9.04 on an older Dell 2.8ghz processor, only 512meg ram.

Myth ran "out-of-the-box", and only needed the "tune.sh" (as described on the wiki page) to run at startup.

Are you using both the analog and digital tuners, or just one?  

If you can't watch the channel, you can't record it.  The card's two tuners need to be set up separately.   The digital selected as DVB and the analog as . . . MPEG2 it think (I can verify later when the backend stops recording).

I'd pick just one of these for now and make sure you can watch the channel first, then worry about recording.


John

---

