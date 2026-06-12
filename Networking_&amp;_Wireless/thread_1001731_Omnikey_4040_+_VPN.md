---
title: "Omnikey 4040 + VPN"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by redhat24 on 2008-12-04
Hi!

I have a Thinkpad Lenovo T61 with an Omnikey 4040 smart card reader (PCMCIA).
With:
```

$ lspcmcia

```
It lists correctly the device (Can't copy the output because it's my father's laptop)

I tried *gnugp* and *poldi-ctrl*, they saw the device, and knew if the card wasn't plugged. But when I plugged the card, it says: "No such file or directory."
I think there's something with the encryption (pkcs#11) or so (as much as i know a card has a "filesystem" aswell, and maybe it can't be read, because can't decode it.) (I installed the packages I think, but definitely I missing something)

If this problem could be solved, my father could switch from xp to ubuntu (he needs the card reader for VPN to connect to his company's network)

Thanks for your help!

---

