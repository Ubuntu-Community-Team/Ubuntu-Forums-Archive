---
title: "SN25P Sound not working from fresh install"
date: 2007-10-04
forum: Multimedia &amp; Video
---

### Post by sabrateur on 2007-10-04
Hello everyone, I'm new to linux, ubuntu feisty is my first distro ever, and I'm having trouble getting sound to work.

I've done everything that the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") advised to do, including rebuilding the alsa drivers.

I started with Feisty 7.04 32bit. Then upgraded to Gutsy 7.10 beta hoping it will fix the sound, but it didn't.

aplay -l gives this:
```
aplay: device_list:204: no soundcards found...
```

lspci -v results in (partially):
```
06:06.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
        Subsystem: VIA Technologies Inc. Albatron PX865PE 7.1
        Flags: medium devsel, IRQ 20
        I/O ports at a000 [size=32]
        I/O ports at a400 [size=128]
        Capabilities: <access denied>
```

modprobe snd-ice1724 gives no error but further aplay -l still says no soundcard.

can't run alsamixer. gives this error:
```
alsamixer: function snd_ctl_open failed for default: No such device
```

please help!

---

### Post by sabrateur on 2007-10-04
I tried loading the feisty livecd, and the result is the same. No soundcard loaded although the modules loaded (according to lsmod) are correct (snd-ice1724).

Now downloading Dapper 6.06 livecd. Will try booting from that and see what happens.

---

### Post by sabrateur on 2007-10-07
Dapper LiveCD gives the same result. Sound card detected, proper modules loaded, but aplay says no soundcard.

I tried an external sound card (Audigy 2 NX) and it works fine. Now I have sound.

But the problem remains, the onboard sound doesn't work. A bug perhaps?

---

