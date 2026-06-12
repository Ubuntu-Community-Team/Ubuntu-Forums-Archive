---
title: "No DHCPACK packets"
date: 2011-06-19
forum: Networking &amp; Wireless
---

### Post by usbrut on 2011-06-19
So I was having trouble connecting via wired on my Ubuntu box, so I did a dhclient command, and saw that the port was being discovered, I was being offered an address, my port tried to request the address... and then my port was being discovered again. Wired was working before I went to sleep. I can't ping the default gateway.

I tried pinging the GW from my Windows box (connected wirelessly). The stats: 6% loss, min 10ms, max 1373 ms, avg 235 ms.

I might be wrong, but this seems kind of weird. /etc/resolv.conf is empty. I'm thinking the DHCP server is just being a pain, but I can't be sure. If it's down, why am I getting DHCPOFFERs? The Windows box can probably still connect simply because it had an address before, so it might be using an old lease. The Ubuntu box restarted (it slept and I hit the power button one too many times :P), so I'm guessing it lost its old leases?

There's stuff that makes me think the DHCP server is down, and there's stuff that makes me think otherwise. What does this stuff make you all think? =)

---

