---
title: "[SOLVED] 8.04 (Hardy Heron) + Edimax USB 7138Ug + Edimax Router BR-6204Wg = Failure"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by t-timmy on 2009-01-18
Hi,

I didn't find this in the forums and I was able to solve this myself, so I thought to share.

I installed Hardy Heron (8.04) using Wubi.
I have a 7138Ug Edimax USB wireless adapter, and a BR-6204Wg Edimax router.
I have WPA pre-shared key protection on the router.

When I attempted to connect, I kept getting prompted for the key even though I entered it correctly.

I solved the issue by completely updating my Ubuntu system using a different network connection, and by upgrading the firmware on my router. I also restarted Ubuntu after the upgrade. 

If you get the same symptoms I suggest you try the same (even if you have a different brand).

---

### Post by t-timmy on 2009-01-18
Goddammit...

I restarted and again it prompts for the passphrase repeatedly.

Any suggestions...?

---

### Post by t-timmy on 2009-01-18
Unplugged USB and plugged it back in, now it works, even after restart.

Weird.

Outputs:

---

