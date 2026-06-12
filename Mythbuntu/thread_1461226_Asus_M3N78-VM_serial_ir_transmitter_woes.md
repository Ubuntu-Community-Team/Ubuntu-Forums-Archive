---
title: "Asus M3N78-VM serial ir transmitter woes"
date: 2010-04-23
forum: Mythbuntu
---

### Post by Prefader on 2010-04-23
I hope to create a slightly more useful title once I start to whittle this issue down . . .

So, I recently upgraded my hardware on a working mythbuntu 9.10 box, and I noticed that I was quickly running out of space on my root partition.  Turns out that the lirc daemon was spamming syslog and daemon.log with:
```

Apr 23 23:05:33 leemyth lircd-0.8.6[2759]: removed client
Apr 23 23:05:33 leemyth lircd-0.8.6[2759]: accepted new client on /var/run/lirc/lircd1
```
over and over and over again (/var/run/lirc/lircd1 is the daemon for my ir transmitter, which was still working at this point), with the logs approaching well over 2 gigs in a little under 15 minutes.  Crazy, right?

After tinkering with things a little bit (and getting absolutely nowhere), I decided that it might be in my best interest to do a reinstall, since the upgrade involved a new motherboard, processor, and RAM, which I know can sometimes make pre-existing installs panic a little.

So, re-install is finished, everything is working . . . except for my transmitter, which is dead, dead, dead: irsend reports no errors, but I get no blinky lights on the transmitter and I'm still plagued by rampant log-growth.

The system:
Asus M3N78-VM
AMD Phenom X3 8750
2GB RAM
PVR350
pcHDTV5500
Mythbuntu Karmic 64

It's late here, and there's a very good chance that I won't see any responses until the morning.  I will provide more information (configs, logs, etc) when I'm not so fracking tired. :)

Thank you.

---

### Post by Prefader on 2010-04-24
Well, everything seems ok now.  Not entirely sure why, though.  I re-configured the transmitter and receiver through MCC, changed config files for my DTA, and poof, everything is ok.  Not sure what I did different from when I initially installed everything, though.

---

