---
title: "Madwifi DPRINTF macro definition"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by legendbb on 2010-02-11
DPRINTF is extensively used in madwifi driver for debugging

ex.         DPRINTF(sc, ATH_DEBUG_DOTH,
            "Set CHANNEL_DFS_CLEAR flag on channel %4u MHz\n",
            channel->channel);

As a newbie I don't understand this macro definition:

#define    DPRINTF(sc, _fmt, ...) do {                \
    if (sc->sc_debug & ATH_DEBUG_RATE)            \
        printk(_fmt, __VA_ARGS__);            \
} while (0)


the above ex. should be replaced as printk(ATH_DEBUG_DOTH, "Set...

How does this "ATH_DEBUG_DOTH, " work for the printk format?

Please suggest!

Thx

---

