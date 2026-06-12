---
title: "WLAN region code fixed to &quot;US&quot;"
date: 2011-11-23
forum: Networking &amp; Wireless
---

### Post by ygoe on 2011-11-23
Hi,

I have a Compex WLM54G wifi card (Mini-PCI) and want to use it on all channels available here (1-13). But for some reason, the card or system think that I'm in the US and disable channels 12-14 (I can see it in dmesg). I've spent a few hours reading everything I could find to change that region code, but nothing had any effect. Does my card support those channels at all? And who is the definitive reference to tell me how it really works? (There are really a lot of people out there who publish things, but in this case, most of it seems to be wrong or outdated. The madwifi driver for instance seems to be history today...)

The ath5k driver was loaded automatically and I can connect to my channel 1 network here, so the card basically works.

Also, I cannot seem to set the tx power to anything above 100 mW. The card should support 200 mW but when I set a value > 100mW, it says "invalid argument". How is that supposed to work?

---

### Post by ygoe on 2011-12-02
On the ath5k website I found that setting txpower is not yet implemented.

For the other issue, I've found another thread now: [http://ubuntuforums.org/showthread.php?t=1860818](http://ubuntuforums.org/showthread.php?t=1860818)

---

