---
title: "No sound with ASRock a75m hvs"
date: 2012-01-28
forum: Mythbuntu
---

### Post by solars on 2012-01-28
Hi there,

Can anyone tell me how to install drivers to make sound work on the ASRock a75m HVS? I'm using it with an AMD a4-3300 and I don't get any sound through the connected HDMI

It apparently has a "5.1 CH HD Audio (VIA® VT1705 Audio Codec"

Would be very thankful if anyone can give me a hint how to proceed, the default intsallation doesn't recognize it.

---

### Post by nickrout on 2012-01-28
> **solars said:**
> Hi there,

Can anyone tell me how to install drivers to make sound work on the ASRock a75m HVS? I'm using it with an AMD a4-3300 and I don't get any sound through the connected HDMI

It apparently has a "5.1 CH HD Audio (VIA® VT1705 Audio Codec"

Would be very thankful if anyone can give me a hint how to proceed, the default intsallation doesn't recognize it.

What version of mythbuntu?
what version of mythtv?

What does ```
aplay -l
aplay -L
```

tell you.

Have you scanned for audio devices in the setup part of mythfrontend?

---

### Post by solars on 2012-01-28
Hi, thanks for your help!

It's the latest version of both, I installed it right now.
aplay -l shows 2 cards it seems:

card: 0 Generic HD Audio Generic, device 3: HDMI 0

card 1: Generic 1 HD Audio Generic device 0: VT1705 Analog

aplay -L shows a lot of info including some lines named 'surround...'

could it be somehow switched to the wrong default card?
how can I change this?

I'm not sure to which configuration setup you are referring, how can I access that?

---

### Post by nickrout on 2012-01-28
In mythfrontend

Utilities/Setup|Setup|General - about the 4th page

---

