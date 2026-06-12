---
title: "IPv6"
date: 2006-07-15
forum: Networking &amp; Wireless
---

### Post by blitzd on 2006-07-15
I've noticed that many people seem to have network problems with IPv6 enabled on Breezy/Dapper. I was experiencing some very slow DNS lookups myself until I disabled it via blacklisting the module. Anyways, I've recently installed SLED to give it a whirl and found that although it has IPv6 enabled by default (as Ubuntu does) that I have no such DNS lookup problems. Anyone happen to know what the root cause of this may be?

---

### Post by coffeecat on 2006-07-16
I had a hell of a time with this IPv6 issue last year. Disabling IPv6 or setting host address and DNS addresses manually worked, but I always thought these to be workarounds (read cludges). Then I updated my router's firmware and the problem melted away. Now I could use DHCP on both my Windows and Linux boxes. I believe inadequate router firmware is confused by IPv6 modified addressing.

---

### Post by blitzd on 2006-07-16
> **coffeecat said:**
> I had a hell of a time with this IPv6 issue last year. Disabling IPv6 or setting host address and DNS addresses manually worked, but I always thought these to be workarounds (read cludges). Then I updated my router's firmware and the problem melted away. Now I could use DHCP on both my Windows and Linux boxes. I believe inadequate router firmware is confused by IPv6 modified addressing.

I updated my router firmware not to long before I installed 6.06, and I'm behind the exact same router with no configuration changes when using SLED. So I'm pretty sure that's not the problem in my case, could be for others though. I'm going to take a closer look at the config differences between Dapper/SLED when I re-install.

---

