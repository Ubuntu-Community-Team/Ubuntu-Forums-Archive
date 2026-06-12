---
title: "Is unplugging the antenna bad?"
date: 2011-11-29
forum: Networking &amp; Wireless
---

### Post by ygoe on 2011-11-29
This may be a bit unrelated to Ubuntu, but this is the closest place I know to ask that question.

When using a WLAN card in a computer with an external antenna, is it a bad idea to unplug the antenna while using the interface? And, for a more common case, is it a bad idea to bring up a wlan interface (configured with ssid and psk) with no antenna attached to the card?

I may want to use my ALIX box in diverse network environments and would prefer Linux finding its way to the network automatically, i. e. without preparing the network configuration manually before changing locations (and unplugging the antenna because I'm going to a wired network). And changing networks is a bit uncomfortable because I mostly have network access to the box only.

If it matters, the card is a Compex WLM54G 23dB mini-PCI with Atheros chipset.

---

### Post by haqking on 2011-11-29
> **LonelyPixel said:**
> This may be a bit unrelated to Ubuntu, but this is the closest place I know to ask that question.

When using a WLAN card in a computer with an external antenna, is it a bad idea to unplug the antenna while using the interface? And, for a more common case, is it a bad idea to bring up a wlan interface (configured with ssid and psk) with no antenna attached to the card?

I may want to use my ALIX box in diverse network environments and would prefer Linux finding its way to the network automatically, i. e. without preparing the network configuration manually before changing locations (and unplugging the antenna because I'm going to a wired network). And changing networks is a bit uncomfortable because I mostly have network access to the box only.

If it matters, the card is a Compex WLM54G 23dB mini-PCI with Atheros chipset.

no and no, the antenna merely gives you your signal strength, even without it you will get some strength though minimal.  you can take it off and re-attach it whilst it is running, i change from a 3 to 5 to 9 to 15 to 30dbi and from omni directional to directional all with it running just fine.

Cheers

---

### Post by ygoe on 2011-11-29
Okay, I was more worrying about possible hardware damage. I know that radios can get hurt when transmitting with no antenna attached. Are wlan devices robust enough to survive that in good health? Will a wlan device transmit anything at all if there's no network it knows (by ssid)?

---

### Post by bluexrider on 2011-11-29
Why would you chance it? Use it the way it was designed.

---

### Post by ygoe on 2011-11-29
If I did that, I needed to attach an antenna all the time, just because that card is built into the box. Even if I don't want to use wireless networks at all because there are none. In devices with a built-in antenna you don't have to think about that.

---

### Post by haqking on 2011-11-29
> **LonelyPixel said:**
> Okay, I was more worrying about possible hardware damage. I know that radios can get hurt when transmitting with no antenna attached. Are wlan devices robust enough to survive that in good health? Will a wlan device transmit anything at all if there's no network it knows (by ssid)?

see attached, first is with a 5 dbi antenna attached, second is after detaching the antenna when running, it drops down to one network and probably would of picked up a few more given time either way detaching it was fine.

I mean dont get me wrong it not a great practice and should be run with an antenna but if you do disconnect when running it is fine.

---

