---
title: "Atheros AR9285 on Eee PC can't see all networks"
date: 2012-06-13
forum: Networking &amp; Wireless
---

### Post by johnwickedson on 2012-06-13
Hey people, you're my last hope. :p
I have an Asus Eee PC 1215B that I formatted and installed Ubuntu. At first, all hardware worked natively. Soon, the internet connection became unstable and eventually, it would no longer connect. The thing is that it only happened when I was using the internet at college. Over there, the network is not exactly password-protected: you connect and then you have to authenticate with the browser (entering an ID and a password). At home the wi-fi always worked as it should.
I tried other distros, like Mint, openSUSE and Fedora, all with the same results: the wireless card can no longer even detect the university's network (only private ones, including my own).
I'm not a total linux noob, but I'm definetely a beginner. I really need some help here, 'cause I don't wanna have to switch back to Windows. The netbook is currently running Fedora 17, but I'll move to Ubuntu 12.04 if that eases the resolution of my issue.

Heres the output of** lspci -v**
```

Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
          Subsystem: Foxconn International, Inc. Device e049
          Flags: bus master, fast devsel, latency 0, IRQ 16
          Memory at fe00000 (64-bit, non-prefetchable) [size=64K]
          Capabilities: <access denied>
          Kernel driver in use: ath9k

```Thanks in advance for your attention,

John

---

