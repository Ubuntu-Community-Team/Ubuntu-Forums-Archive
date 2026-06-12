---
title: "ath_pci/ath5k freezing on load"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by danzik17 on 2009-03-24
So I'm completely unable to load either ath_pci or ath5k.  Both freeze up my computer immediately on doing modprobe -v <module>.  The only way for me to even boot my computer is to edit /etc/modprobe.d/blacklist and add an entry for ath_pci.

The issue occurs on both x86 and x86_64 versions of 8.10.  I haven't tried previous versions yet, I'll be giving that a shot tomorrow but wanted to get this thread out there in case anyone had idea/tips.

I have compiled/installed from source for each of those modules.

Any tips on where to start?  No error messages are available at all since this is a hard freeze which is a bit annoying.

I should note that 8.10 works fine on my laptop (T41) which has an Atheros chipset in it for wifi.

---

### Post by kevdog on 2009-03-24
What chipset do you have 

lspci -nnm

---

### Post by danzik17 on 2009-03-24
Wifi Chipset:

Atheros AR5001X+

Onboard Chipset:

Intel G965

Trying a rollback to 8.04 x86_64 to see if it's an issue only in the latest version.

---

### Post by danzik17 on 2009-03-24
Rollback to 8.04 did not fix the issue.  It must be specific to my hardware or a combination of hardware since 8.10 works fine on my laptop which is also using an Atheros chipset.

---

### Post by kazik on 2009-04-14
I have similar issues with ar5212 on hardy. Had to blacklist ath_pci to be able to boot with the PCI card inserted. Then, I installed linux-backports-modules-hardy and got ath5k, but now it freezes again (after loading ath5k_pci).

---

### Post by mathemagician on 2009-05-02
I think this is the same problem that I'm having.
I'm running Jaunty 64bit, ASUS P5Q mobo, Q8400.
lspci:
```
05:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
```

Any luck?

---

