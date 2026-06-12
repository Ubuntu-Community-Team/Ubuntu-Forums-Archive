---
title: "Mandriva WI-FI"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by galacticcraft on 2008-12-28
\\:D/8-):-kPlease
The following trouble I have with the Wireless D-Link-300,DWA-510 & Mandriva-2009:need drivers for installing wi-fi-connection  with one OS- Mandriva ,the other one-Windows.
If somebody has a hint of troubleshouting ,don't be severe-drop them

---

### Post by albinootje on 2008-12-28
> **galacticcraft said:**
> \\:D/8-):-kPlease
The following trouble I have with the Wireless D-Link-300,DWA-510 & Mandriva-2009:need drivers for installing wi-fi-connection  with one OS- Mandriva ,the other one-Windows.
If somebody has a hint of troubleshouting ,don't be severe-drop them

Please post the output of :
```

lspci
lsusb
rpm -qa|grep -i ndis

```

---

