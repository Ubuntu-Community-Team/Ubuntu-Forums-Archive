---
title: "Slow/dropping wireless on Acer A150 - 10.04 NBE"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by Society on 2010-05-16
Acer Aspire One A150 (aka ZG5) originally supplied with Linpus Lite (with which everything worked) but NBE 10.04 now installed from ISO (on UNetBootin-prepared memory stick) which uses ath5k driver for the Atheros AR5001 wireless.

Wireless originally just didn't work (wireless not enabled) but now (see below for steps on the way) usually either doesn't connect or else works for a very short while but doesn't maintain the connection (even if as simple as possible with no security) for more than a minute or so. It usually takes a good while to auto-reconnect and then drops again.

System > Administration > Hardware Drivers states "No proprietary drivers are in use on this system.

While connection is up, nm-tool reports AP as having 54Mb/s rate and strength of 100 but speed capability varies wildly and can be as low as 1 Mb/s.

I've searched widely for solutions and the amendments I've made since the original "not enabled" condition include those involving:
linux-backports-modules-wireless-lucid-generic and
bcmwl-kernel-source package

I've attached no significance to the lights (or lack thereof) associated with the physical wireless slide-switch as it seems to signify little (if anything) and so have no record of if/when there was any flickering or solid light.

Any other clues for a noob would be much appreciated.

---

### Post by ivan.baldinotti on 2010-05-17
Hi, I have the same problem with the same hardware and the same version of Linux. In windows all work fine.

---

### Post by ivan.baldinotti on 2010-05-23
I just solved installing ndiswrapper and the windows drivers. Now the connection is fast and stable as in windows.

---

