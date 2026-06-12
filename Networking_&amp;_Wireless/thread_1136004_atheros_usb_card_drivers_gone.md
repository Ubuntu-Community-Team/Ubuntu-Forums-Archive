---
title: "atheros usb card drivers gone"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by alimahmoudy on 2009-04-24
Good evening, i was trying to apply a patch to my atheros card, i downloaded patched drivers and replaced the existing ones,
via the copy command.
I'm using kernel 2.6.24-23

I copied the patched files via those commands:

```
cp -R ieee80211 /lib/modules/2.6.24-23-generic/kernel/net/
```

```
cp -R zd1211rw /lib/modules/2.6.24-23-generic/kernel/drivers/net/wireless/
```

I did a dumb mistake by not backing up those folders before copying.

Can you help me ?

Also, i can't get the card to work on kernel 2.6.27.
I'd appreciate the help, thanks in advance.

---

