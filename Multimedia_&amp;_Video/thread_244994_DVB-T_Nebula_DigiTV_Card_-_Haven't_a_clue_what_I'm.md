---
title: "DVB-T Nebula DigiTV Card - Haven't a clue what I'm doing"
date: 2006-08-27
forum: Multimedia &amp; Video
---

### Post by moeFinley on 2006-08-27
Does this tell me that my card is setup correctly?

```
$ dmesg | grep card
[17179572.152000] isapnp: Scanning for PnP cards...
[17179572.532000] EISA: Detected 0 cards.
[17179598.588000] bttv: Bt8xx card found (0).
[17179598.588000] bttv0: detected: Nebula Electronics DigiTV [card=104], PCI subsystem ID is 0071:0101
[17179598.588000] bttv0: using: Nebula Electronics DigiTV [card=104,autodetected]
```

What are these modules and when do I need to load them?

modprobe dvb-btxx
modprobe mt352

MythTV says "Could not open card #0!"

People in these forums seem to have more luck with Kubuntu and Kaffeine, is it worth switching?

---

