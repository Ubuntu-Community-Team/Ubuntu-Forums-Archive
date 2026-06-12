---
title: "[SOLVED] /dev/lirc is missing after mytbuntu-lircrc-generator update from 0.16.to 0.1"
date: 2007-12-02
forum: Mythbuntu
---

### Post by kruel on 2007-12-02
After updating mythbuntu-lircrc-generator from 0.16 to 0.17 today, my remote stopped working.

I ran lircd manually, and it crashes when a client tries to register with it.  It dumps an error that states that it cannot find /dev/lirc.

Sure enough, when I check /dev  I only have lircd and lircm -- and I know /dev/lirc used to exist.

I cleared out all my lirc configs, and started from scratch, reconfigured it in the Command-Center.  And it still has this problem,  I even tried reverting back to 0.16 with no success.

Has anyone else run into this problem?

Please help, I miss my remote :(

Thank you.

---

### Post by superm1 on 2007-12-03
The change to mlg 0.17 only affects .lircrc files.

What remote are you using?  Does the driver load (according to lsmod)?

---

### Post by kruel on 2007-12-03
Thank you for the reply.

I played with things a little more this morning, I got it working.

I checked 'lsmod' and it was not loading the second module lirc_l2c if I remember correctly.

I shut the machine down and swapped the card to a different PCI slot, booted it up, and it worked.  The only thing I can think is that the card got fuzzed when I rebooted after updating.

Please mark as solved.

Thank you again.

---

