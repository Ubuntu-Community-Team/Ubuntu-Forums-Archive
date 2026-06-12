---
title: "Restriction with MAC vs. WPA2?"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2010-01-08
Trying to get my 802.11n router and Asus to play nice and give me the faster transfer speeds I'm *supposed* to be getting, I began to wonder this: why should I use a password of any kind if I set my router to only allow certain MAC addresses access?

Any input?

Oh, and somewhat unrelated, anyone have an idea why iwconfig is telling me my bitrate is 0?

---

### Post by changingstate on 2010-01-08
Easy, I can sniff MAC addresses off an unencrypted network and spoof them inside two minutes. Turn the encryption on if you can, even WEP is better than nothing.

---

### Post by moore.bryan on 2010-01-08
I have WPA2 (AES) and a very complicated string, so I was just wondering why not just MAC alone was good enough. Your answer was *enlightening*; thanks changingstate!

Now, I've seen video of a conference where Mark Shuttleworth "went off" about passwords vs. authentication. I have a simple understanding of that method and employ is with my ssh connections. In theory, wouldn't I be able to do the same thing between my lappie and router?

---

### Post by changingstate on 2010-01-08
As I understand things, yes, it can be done, though it's not something I've practical experience with. You'd want to head in the direction of EAP-TLS, apparently wpa supplicant and wicd support it.

---

### Post by moore.bryan on 2010-01-09
Unfortunately, it would seem to get my D-Link router to use 300mb/s at 802.11n, I *have* to use WPA2 (AES). Oh well, it was a nice fiction.

---

