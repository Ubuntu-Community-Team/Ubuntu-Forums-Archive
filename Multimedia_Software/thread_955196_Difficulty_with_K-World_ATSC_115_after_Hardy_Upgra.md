---
title: "Difficulty with K-World ATSC 115 after Hardy Upgrade"
date: 2008-10-22
forum: Multimedia Software
---

### Post by Kepesk on 2008-10-22
Hello!

I have a Xubuntu machine that I use for MythTV that I recently upgraded from Gutsy to Hardy.  Ever since I did that, my video input card doesn't work!

I have a K-World ATSC 115 which I use with an antenna to grab over-the-air ATSC signals.  Before I upgraded from Gutsy, I got four stations perfectly (100% signal) and another five okay (90-95% signal).   Ever since the upgrade, when I try to watch TV, MythTV never gets to the full 100%, and never locks onto any channel.  The highest it gets is 99% signal, and it complains either of No Lock or Partial Lock with (L__) or (LA_) displayed, respectively.

I've tried completely removing the card from MythTV and re-adding it, but when I scan for channels, all of the channels I used to get come up with "No Tables".  I've tried watching TV with MPlayer, but it doesn't lock on either.  This suggests to me that it may be a driver issue and not a Myth issue.

None of the logs are any help either.  The the Myth backend log simply responds as if I didn't get an adequate signal, along with every other log I've checked.

I've hunted far and wide on the internet for a solution.  The closest I've found is the thread at [http://www.gossamer-threads.com/lists/mythtv/users/337610#337610]("http://www.gossamer-threads.com/lists/mythtv/users/337610#337610") in which, halfway down, someone with Xubuntu encounters what appears to be the same problem with the same card, and fixes it by reinstalling the firmware.  I tried this procedure, but it didn't change anything for me.

Does anyone else have any ideas on this?

Thanks!

---

### Post by Kepesk on 2008-10-22
Okay, I though I'd post some specifics on this.  My /etc/modprobe.d/saa7134.modprobe is this:

```
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=90 disable_ir=1
```

Which seems to be correct according to several sources.  'dmesg | grep nxt' gives:

```
[   57.108128] nxt200x: NXT2004 Detected
[   57.148105] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   57.909336] nxt2004: Waiting for firmware upload(2)...
[   59.457284] nxt2004: Firmware upload complete
```

This also seems to be correct, according to several sources.  The only anomaly I've found is in 'dmesg | grep saa' which reads:

```
[   56.118991] saa7130/34: v4l2 driver version 0.2.14 loaded
[   56.119498] saa7133[0]: found at 0000:04:07.0, rev: 209, irq: 16, latency: 32, mmio: 0xfddff000
[   56.119504] saa7133[0]: subsystem: 17de:7352, board: Kworld ATSC110/115 [card=90,insmod option]
[   56.119515] saa7133[0]: board init: gpio is 100
[   56.251570] saa7133[0]: i2c eeprom 00: de 17 52 73 ff ff ff ff ff ff ff ff ff ff ff ff
[   56.251578] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   56.251583] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   56.251588] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   56.251593] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   56.251598] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   56.251603] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   56.251607] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   56.533758] tuner 2-0061: chip found @ 0xc2 (saa7133[0])
[   56.623354] saa7133[0]: registered device video0 [v4l2]
[   56.623376] saa7133[0]: registered device vbi0
[   57.139869] saa7134 ALSA driver for DMA sound loaded
[   57.139910] saa7133[0]/alsa: saa7133[0] at 0xfddff000 irq 16 registered as card -2
[   57.141135] DVB: registering new adapter (saa7133[0])
```

This seems to be much longer than most other threads indicate it should be.  In particular, I've never seen a reference to the eeprom lines anywhere else.  Could this be related to the problem?

Thanks in advance!

---

### Post by Kepesk on 2008-10-22
One more tidbit of information; I just replaced the KWorld card with an identical one, and that was no help, so I know it's a software issue and not a hardware issue.

---

### Post by Kepesk on 2008-10-25
Okay, I think I'm getting closer on this one.  I've tried a couple of things, and I have a couple more symptoms of the problem to add to the mix.

I tried reverting back to the old Gutsy kernel version, and that had no effect.  Also, I tried compiling the video4linux drivers from scratch.  Again, no change.

The first new symptom I've discovered is that my ATSC signal strength doesn't appear to change for any of the channels I have configured, no matter what I do.  I can unplug the signal amplifier, plug it back in, or unplug the antenna altogether, and there is no signal strength change for any channel.  This suggests to me that the KWorld card isn't being detected properly.

This thought was reinforced by my second discovery: when I add the DVB input for the card to MythTV, it detects the card as an 'Air2PC v2'.  And no matter what I try (removing and re-adding the card, reinstalling drivers), I can't get it to detect it as a KWorld card.  I've never had an Air2PC card, so this is quite the mystery.  Has anyone else ever seen this issue?

Thanks!

---

### Post by Kepesk on 2008-10-26
Okay, after doing more research, it looks like a KWorld 115 being detected as an Air2PC is normal, and shouldn't impact the functionality of the card.

However, further research suggests that my issue may be fixed with an older version of the nxt2004 firmware; the newer version may have issues with my card.  Unfortunately, getting my hands on an older version has proven very difficult.  Poking through old kernel versions reveals that the scripts you use to get the firmware simply download a current version from a website.

Would someone be able to point to a place where I could find an old version of the nxt2004 firmware, or be able to provide it themselves, say from the Feisty era?

Thanks!

---

