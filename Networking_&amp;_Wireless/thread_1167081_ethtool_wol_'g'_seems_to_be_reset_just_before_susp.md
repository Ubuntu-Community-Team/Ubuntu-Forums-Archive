---
title: "ethtool wol 'g' seems to be reset just before suspend"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by Meson on 2009-05-22
On a particular computer I have
```

$ sudo ethtool -s eth0 wol g

```

Worked fine with Intrepid.  I could suspend the computer and wake it up with a Magic Packet.

After downgrading to Hardy, the same command works just fine (I can confirm that the 'g' flag is actually set), however the computer does not respond to WOL.

When I manually bring it back up, the WOL flag is now set to 'd'.  I can reset it back to 'g' manually, but I can't figure out what is resetting it.

Again, I know it works with this hardware.  Also, I'm only trying to WOL from suspend - not from a powered off state.

---

