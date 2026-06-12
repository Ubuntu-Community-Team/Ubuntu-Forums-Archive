---
title: "How to use 802.11g only?"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by various-buddhist-monks on 2010-05-21
I'm wondering if there's a way to use 802.11g only, even when 802.11n is also available.

I am running Ubuntu 10.04 LTS on a EEEPC 1201n, and having wireless problems as expected given the lack of good support for that chipset. 802.11g+b support works fairly well. By contrast, 802.11n will connect but does nothing afterward.

I have a Draft-N router at the house, and I don't want to slow down other computers just because this one can't handle N. Is there a way to get the wifi driver to skip N and use only G or B?

Thanks.

---

### Post by wheredidrealitygo on 2010-05-21
Please post the output of ```
iwlist modulation
```

If it says unknown, or no modulation available, then the driver of your wireless card won't support permanently changing the card to only work on one modulation (b/g/n), let's hope your driver supports it.

I believe your card is an rtl8191, though detected as 8171.

---

### Post by various-buddhist-monks on 2010-05-21
Well, nuts.

```
wlan0     unknown modulation information.
```

Guess I'll just have to wait until the driver gets updated to properly support N?

---

### Post by wheredidrealitygo on 2010-05-21
It's not necessarily that your driver doesn't support N, it likely does, it's just your driver doesn't support locking the card into one modulation only.

Some draft-n routers can do dual ESSIDs, one being for B/G, and one for N. Does yours have that option or can you enable it? That way you could have one network for the N machines, then that one other network for the G machine, and keep them on separate channels to distinguish them, even though they'd technically be on the same LAN for file sharing and such.

Aside from that not really much you can do.

---

