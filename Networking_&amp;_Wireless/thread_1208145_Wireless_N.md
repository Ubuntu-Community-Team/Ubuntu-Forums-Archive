---
title: "Wireless N"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by doubad on 2009-07-08
Hey guys, I've been searching but I can't seem to find any recent answers to this.
I just bought a D-Link Xtreme N desktop adapter (DWA-552) and I've noticed that jaunty hates it... alot.
Is there any answer to this, I've been getting mixed messages from what I've been reading, some saying madwifi and ndiswrapper are bad and some saying they don't work. All of that info seems dated though.
Anyone know if theres been progress? if theres a patch or something?

---

### Post by pytheas22 on 2009-07-08
It's hard to determine much knowing only the name the device is sold under.  Many manufacturers of wireless cards change the insides significantly but still sell the devices under the same name.  So your DWA-552 may not be the same as the other DWA-552s you've read about.

To let us know for sure what kind of hardware you have, please run these commands in the terminal:
```

lspci -nn
lshw -C Network
uname -rm
```

With that information, we can figure out the best way to make your device work.

---

