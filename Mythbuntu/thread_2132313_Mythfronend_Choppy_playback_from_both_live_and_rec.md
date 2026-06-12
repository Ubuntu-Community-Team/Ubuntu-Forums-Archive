---
title: "Mythfronend Choppy playback from both live and recorded programs"
date: 2013-04-04
forum: Mythbuntu
---

### Post by TheFuzz4 on 2013-04-04
Hey Everyone,

Now onto my next problem.  I have a Foxconn Nettop box that I use as a frontend.  My backend is a HP DL385 G2 that lives in my crawlspace.  I have 5 tuners on the backend a Hauppage 2250 on the inside of the server and a HD HR Prime w/cable card 3 tuner as well.  The backend is working fine and I cannot find any problems with it.  

However, this particular frontend has an issue all of a sudden.  I am currently running Myth 26 on everything.  This problem just started this week.  No matter what we watch (I haven't tried movies yet) the playback is choppy as all hell and eventually the playback just quits.  I do have the box on my WiFi at home on its own N router all by itself.  To rule out the network issue, I have the frontend installed on my laptop as well and it plays things back just fine on the same connection.  I also tried it out on my desktop over the LAN and no issues there so this is limited to just this one front end.

The box has the following hardware
CPU Type: AMD E-350 APU (1.6GHz, Dual-Core)
North Bridge: AMD Hudson D1Memory slot: 1 x 204Pin Memory Type Supported: 4GB
Serial ATA: 1 x SATA 3.0Gb/s
Onboard Video: AMD Radeon HD 6310
Front USB: 2 x USB 3.0, Rear USB : 4 x USB 2.0
4GB of Ram

While doing playback I have tailed the logs of the frontend and see this over and over
```

Apr  4 08:06:18 myth1 mythlogserver: mythfrontend[1447]: N CoreContext mythplayer.cpp:2093 (PrebufferEnoughFrames) Player(0): Waited 104ms for video buffers AAAAAAAAUUAUUUUuUULUUAAAAAAAAAAP
Apr  4 08:06:18 myth1 mythlogserver: mythfrontend[1447]: N CoreContext mythplayer.cpp:2093 (PrebufferEnoughFrames) Player(0): Waited 208ms for video buffers AAAAAAAAUUAUUUUuUULUUAAAAAAAAAAP
Apr  4 08:06:18 myth1 mythlogserver: mythfrontend[1447]: N CoreContext mythplayer.cpp:2093 (PrebufferEnoughFrames) Player(0): Waited 103ms for video buffers AAAAAAAAAAAAAAAUAAUUUuUULUUAUuAP
Apr  4 08:06:18 myth1 mythlogserver: mythfrontend[1447]: N CoreContext mythplayer.cpp:2093 (PrebufferEnoughFrames) Player(0): Waited 209ms for video buffers AAAAAAAAAAAAAAAUAAUUUUUULUULUUAP

```

I have googled this as much as I can with no viable solution.

I know that you can expect these errors right at the start of the stream but once it gets going they should be non existent. 

The only thing that I haven't tried yet is a reinstall of the box but I really don't want to go down that road if I can avoid it.  Getting the audio back out over the HDMI is a PITA.  Thanks.

Thank you all for your help with this in advance.

---

### Post by TheFuzz4 on 2013-04-05
Ok so after screwing around with the Playback profiles for a bit I finally found a good combo that now works.  The logs show some buffer issues right at the start of a stream or when skipping around in either Live or a recording but once it starts going then its fine.  Not really sure what caused the issue with this but I'm glad to have my TV back to 100% and a happy wife :).

---

