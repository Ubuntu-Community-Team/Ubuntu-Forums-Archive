---
title: "Kubuntu 7.10 + VIA VT8233 = No Sound?"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by shimrah on 2008-01-24
Hey there,

I'm trying out Kubuntu 7.10, but am having trouble getting sound. Mixers, etc. seem to think they know what my card is, and have it configures, but no sound! Anyone else have troulbe w/this card?

```

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>
```

Thanks in advance!
Shimrah

---

### Post by balaknair on 2008-01-24
Try these steps

1) Load the snd-via82xx module
```
sudo modprobe snd-via82xx
```

2) Now check your sound(In Konsole type alsamixer, and check to see that all channels are unmuted(they are muted by default).

3) If it works,
```
sudo nano /etc/modules
```

and paste this as the last line, save and exit
```
snd-via82xx
```

For further instructions/ troubleshooting please check this thread
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

If your problem is solved, please reply and tell us what worked for you, and mark this thread as solved.

all the best

---

