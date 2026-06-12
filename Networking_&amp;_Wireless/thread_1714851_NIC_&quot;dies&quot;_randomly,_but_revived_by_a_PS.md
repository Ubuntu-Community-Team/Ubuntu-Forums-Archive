---
title: "NIC &quot;dies&quot; randomly, but revived by a PSU reset"
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by jugammel on 2011-03-25
My NIC "dies" randomly, usually during bootup. I can revive it by on-offing my PSU, but it doesn't last.

I had a similar problem on Windows 7. I fixed it by going into the power management settings and disabling "turn off NIC to save power" (or something along those lines). But I cannot find such an option in Ubuntu, assuming the problem is the same in the first place.

Note: This only happens with Ubuntu (since I fixed for Windows 7) so it is not a coincidental NIC failure.

Please help!

---

### Post by anttir on 2011-03-26
I have same problem with Asus P7P55D with Dualboot XP / Ubuntu. Seems XP turns off the network adapter for good or sets it in "wait for lan wakeup" and Ubuntu drivers are unable to turn the adapter back on.
The trademark for this problem is that reset does not enable the adapter but only PSU on/off.

This is a common problem with some chipsets.

I was able to get rid of this problem by toggling "wake-on-lan" settings (tried both on/off) in XP, not in Ubuntu.:)

---

