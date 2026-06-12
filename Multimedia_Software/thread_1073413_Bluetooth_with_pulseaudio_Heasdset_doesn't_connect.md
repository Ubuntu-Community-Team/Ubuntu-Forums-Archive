---
title: "Bluetooth with pulseaudio: Heasdset doesn't connect as sink/source but a2dp"
date: 2009-02-18
forum: Multimedia Software
---

### Post by S-Holzhauer on 2009-02-18
I use a Plantronics P590 Bluetooth headset and configured my audio settings with pulseaudio.
My .asoundrc contains:

```
pcm.bths {
    type bluetooth
    device "00:19:7F:18:C6:A7"
    profile "voice"
}
```

When I type
```

pactl load-module module-alsa-sink device=bths
```

pulseaudio crashes ("Connection failure: Connection terminated"). It works fine with

```
pcm.bths {
    type bluetooth
    device "00:19:7F:18:C6:A7"
    profile "auto"
}
```

But this way the headset is paired as a2dp (audio sink only) instead of headset (both audio sink and audio source).

Switching the headset into pairing mode, and then firing off the pactl commands to pair the headset doesn't work either.

Any suggestions?

---

### Post by pangloss on 2009-05-29
Any progress or news on this? My Jabra BT530 also supports both a2dp and hsp profiles, but I can't get it to use anything other than a2dp, which causes attempts to use the mic (with Skype, for example) to fail. I've also tried the following in ~/.asoundrc w/ no luck:

```
pcm.bthandset {
type bluetooth
device XX:XX:XX:XX:XX:XX
profile "voice"
}
```
FYI this is with Jaunty.

---

### Post by favst on 2009-06-28
Same thing with my Sony DR-BT22.

---

