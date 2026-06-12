---
title: "Live TV Logout and Signal Issues"
date: 2010-11-05
forum: Mythbuntu
---

### Post by Sum Guy on 2010-11-05
I'm currently using Mythbuntu 10.10 on a combined backend/frontend, but set up to allow external frontends. I've installed a dual tuner (DTV2000DS) and it appears to be working. However, I'm having a couple of problems. First, when I try to tune a HD channel, the frontend logs me out. This appears to be unlike other instances of this error, because SD Digital works fine. On a suggestion in another thread, I changed the playback profile to VDPAU High Quality from the default (CPU+), which caused it to exit Live TV with an error on SD Digital and lock up on HD. 

The other problem I'm having is with the signal. Using the same antenna setup which has worked perfectly with a number of other tuners, even on a splitter, I can only see one multiplex, the signal level often drops to 0%, and the SNR never changes from 0% when scanning for channels. The strange thing is that on this multiplex, the tuners appear to work fine. Could it be a signal issue because of the dual tuner?

Any help is appreciated.

---

### Post by LowSky on 2010-11-05
This issue seems to be happening to a good deal of people with various components.

I hope one of the devs knows whats going on. I'm thinking an recent update is causing the issues.

 CPU+ never worked well for me, I used High Quality and that worked better.

As for the signal issue. you can always try a pre-amp to boost the signal

---

### Post by Sum Guy on 2010-11-06
Thanks for suggesting that playback profile, it fixed the issue.

As for signal, I noticed in Live TV that Signal to Noise is 2dB, even though it is always 0 when scanning for channels, with signal strength around 30%. Additionally, I checked the signal strength of a couple of channels on a set top box (same antenna of course) and I found that the multiplex it does see is has substantially lower signal strength compared to some it can't see. Not only that, but I rescanned for channels, and it found another, very weak multiplex (40% signal, even though its weaker on the set top box), but none of the strong ones. Does this sound like software, or hardware? Thanks.

EDIT: That new multiplex doesn't seem to work in Live TV.

---

### Post by Sum Guy on 2010-11-07
Cards are now running perfectly - I generated a channels.conf file using the appropriate part of the procedure detailed here: [http://parker1.co.uk/mythtv_dvb.php](http://parker1.co.uk/mythtv_dvb.php) and imported it. It's the channel scanner, not the signal strength, that is faulty.

---

