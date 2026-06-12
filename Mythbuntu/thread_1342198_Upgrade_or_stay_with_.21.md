---
title: "Upgrade or stay with .21?"
date: 2009-11-30
forum: Mythbuntu
---

### Post by badger_fruit on 2009-11-30
Hey fellow mythbuntu people. I hope someone can help me please!
I have a totally working Mythbuntu 9.04 setup and recently installed Fedora 11 onto my clients. When I try to add Myth front-end onto the clients, it puts v22 on and complains that the schema of my backend is old.

My concern is that if I upgrade my back-end, I will loose recordings or things won't work anymore so I am reluctant to just dive in.  Would, in your opinion, it be worth upgrading or trying to figure out how to install the older front-end on my clients instead?

---

### Post by wackston on 2009-11-30
My advice: if you don't have any major limitations getting the best from your existing hardware I would wait for 0.22 to settle some more. I've just been through upgrading my 0.21 9.04 based setup (one master server with 2X DVB-S and 2X DVB-S2 cards, 3 front-ends) to a 0.22 9.10 based one.

The driver for me was DVB-S2 support for the free-to-air HDTV channels coming on stream here in Germany/UK.

The experience:

* Damn but its easy to accidentally upgrade the dB format before you really want to. Make Backups, make plenty of backups.

* Oddities in RANDR based mode switching (preview window in program guide sometimes a tiny portal on full-size image). These matter for HDTV as for a decent TV you want to switch to native 720p/1080i/1080p according to the source material.

* DVB-S2 support basically works but there are still plenty of rough edges. For example...

[INDENT] There doesn't seem to be a way to use the DVB-S2 cards for DVB-S channels without also allowing the backend to try-and-fail to tune DVB-S2 channels with [/INDENT] 

[INDENT] There's some oops in the Internal H.264 decoder lib that causes what appears to be decoding glitch at the end of each group-of-pictures for some H.264 encoding profiles (yep, you guessed it ... the ones used by the DVB-S2 channels I most wanted to watch) ;-)[/INDENT]

[INDENT] There appears to be now way to switch HDTV display mode''frequency''.   This is a PIA here in Europe as most "native" material is 50Hz but there is plenty of 60Hz material you might want to watch.  Going to the desktop to click on nvidia-settings (or whatever) confuses the desktop and is somewhat uncool. [/INDENT]

[INDENT] Subjectively the front-end just seems somewhat less stable/more prone to crash out when you 'push' it (tune to dead or noisy/corrupted signals, rapid clicking around the GUI etc). [/INDENT]

---

