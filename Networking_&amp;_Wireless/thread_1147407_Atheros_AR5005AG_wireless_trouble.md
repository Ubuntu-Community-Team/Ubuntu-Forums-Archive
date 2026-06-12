---
title: "Atheros AR5005AG wireless trouble"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by liberalist on 2009-05-03
Hi everyone,

I tried out Kubuntu Jaunty Jackalope in a live CD environment, but I cannot connect to the internet. In previous Kubuntu releases (8.04 and 8.10) this always worked without a hitch. I have an Atheros AR5005AG wireless card, for which proprietary drivers were needed in 8.04 and 8.10. However, in Jaunty it says they aren't needed in most cases. I tried connecting with and without proprietary drivers (madwifi). 

The problem might be caused by the new network management plasmoid, how can the old knetworkmanager be added to the tray? Or how can I connect to my wireless network? It is WEP (64-bits) encrypted and broadcasts its SSID. Does it have something to do with [this bug]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/339313")? I am a bit confused about what to do and some solutions seem quite cumbersome.

All my praise goes to the Kubuntu team for delivering such a fine OS, thank you very much.

---

### Post by liberalist on 2009-05-04
I now know it might have something to do with the kwalletd service being disabled on some machines. How can I enable/run kwalletd? I tried Alt+F2 and then type kwalletd and sudo kwalletd and clicked on run, but that did not work.

---

### Post by liberalist on 2009-05-05
I have solved the problem by adding the required information to the /etc/network/interfaces file manually. My file now looks like this (replace yourssid and your_key respectively) and my connection works:

```
auto lo
iface lo inet loopback
auto wlan0 inet dhcp
wireless-essid yourssid
wireless-key your_key
```

---

