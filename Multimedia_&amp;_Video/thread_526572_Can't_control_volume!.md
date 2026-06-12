---
title: "Can't control volume!"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by icherfas on 2007-08-15
Well, my sound works perfectly. Other then the fact that i cannot control the volume either louder or quieter or mute it. It is always at the same level!

 Thank You,
  Igor

---

### Post by duffrecords on 2007-08-15
Could you please post some information about your sound card?  Run the following command in a terminal:
```
lspci
```

---

### Post by icherfas on 2007-08-16
Sure,

```

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)

```

---

### Post by duffrecords on 2007-08-16
What's the manufacturer and model number of the sound card?  Also, could you post the results of this command?
```
sudo lshw -C sound
```

---

### Post by duffrecords on 2007-08-16
Also, you want to check Synaptic Package Manager to see if alsa-base and alsa-utils are installed.

---

