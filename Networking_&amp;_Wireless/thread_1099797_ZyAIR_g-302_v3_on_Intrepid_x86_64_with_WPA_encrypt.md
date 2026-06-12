---
title: "ZyAIR g-302 v3 on Intrepid x86_64 with WPA encryption"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by t0bias on 2009-03-18
Hi everybody,

I've got a new ZyAIR g-302 v3 on intrepid, amd64 (x86_64) and want
to join my wpa-psk encrypted wlan. the rtl8180-module is automatically
loaded and detects my network correctly.

When trying to connect, the connection never establishes, though and
the syslog repeatedly sais "Authentication with xx:xx:xx:xx:xx timed out.".

According to the Ubuntu-Wiki [here]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsZyxel"), ndiswrapper should be used in order to operate this card (although I'm not
sure whether this information is still correct?).

If I try to use ndiswrapper with either the ZyXEL or the Realtek driver for WinXP64, ndiswrapper crashes on module-loading giving a stack-trace and the system hangs forever.

Any ideas?

Thanks,

Toby

---

