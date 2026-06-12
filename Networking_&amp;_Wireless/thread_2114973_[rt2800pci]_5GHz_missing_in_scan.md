---
title: "[rt2800pci] 5GHz missing in scan"
date: 2013-02-11
forum: Networking &amp; Wireless
---

### Post by jamireh on 2013-02-11
I'm running elementaryOS 0.2 beta which is based on Ubuntu 12.04 LTS with a Ralink 3592 wireless card on kernel 3.7.6.

I'm currently in a room which can has several 2.4GHz and 5GHz frequency according to inSSIDer in Windows. 

```
iwlist wlan1 channel
```

This list channels varying from 2.4GHz channels all the way to 5GHz so the driver (rt2800pci) supports it. 

```
nm-tool
```

This only lists frequencies that are 2.4x and completely misses 5GHz. This causes constant drops in this particular area because it's highly populated (university theater hall). 

I've tried the proprietary Ralink drivers and ndiswrapper. The proprietary drivers cause a kernel panic because they're based on the 2.x kernel and ndiswrapper doesn't load the Windows driver properly. 

Does anyone have any recommendations?

---

### Post by G4 Man on 2013-02-23
I have the exact same problem, I've looked around and found no solution. Please keep me posted if you find anything.

---

