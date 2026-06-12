---
title: "Sounds not working after rebooting with card removed"
date: 2007-05-12
forum: Multimedia &amp; Video
---

### Post by jimbone on 2007-05-12
Hi,

I recently booted my computer without my sound card plugged in.  After plugging it back in and rebooting I am am no longer able to play sound.  Peculiarly, alsamixer still works fine, and the driver appears to be loaded (snd-ice1724).

Applications however just do not play sound.  They don't play at all (even with muted sound).  Basically I press the play button and nothing happens (eventually the application appears to freeze).  In amarok the spectral analyzer will display normally for about half a second, and then will halt in the same manner I just described.  Running the applications from a terminal does not produce any unusual output.

My sound card is an m-audio revolution 7.1, based on the envy24ht chipset.

For reference:
```
01:0a.0 Multimedia audio controller [0401]: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller [1412:1724] (rev 01)
        Subsystem: VIA Technologies Inc. M-Audio Revolution 7.1 [1412:3630]
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at d000 [size=32]
        I/O ports at d400 [size=128]
        Capabilities: [80] Power Management version 1
```

Any help would be appreciated.

---

### Post by jimbone on 2007-05-12
bump

---

### Post by jimbone on 2007-05-12
bump + info:

I purged alsa-base and reinstalled it.  That didn't help at all.  Drivers still load up fine.  I also cleared out my .asoundrc file.

Any help would be appreciated.

---

### Post by jimbone on 2007-05-13
anyone?

---

### Post by jimbone on 2007-05-13
I'll try bumping one last time...

---

### Post by jimbone on 2007-05-16
bump

---

### Post by dbd on 2007-05-20
Does it work if you boot with the Live CD? (If it doesn't then it may be a hardware issue)

Have you tried putting it in different PCI slots?

This thread may be of use to you:
[http://ubuntuforums.org/showthread.php?t=400268](http://ubuntuforums.org/showthread.php?t=400268)

Good luck

---

