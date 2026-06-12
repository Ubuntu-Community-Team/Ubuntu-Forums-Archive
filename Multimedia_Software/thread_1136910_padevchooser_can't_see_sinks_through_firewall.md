---
title: "padevchooser can't see sinks through firewall"
date: 2009-04-25
forum: Multimedia Software
---

### Post by Defrector on 2009-04-25
Problem: padevchooser can't see sinks on the network while firewall is on (via firestarter).

Situation involves a somewhat-thin client X11-connecting to a server, and applications on the server stream audio to the thinClient. padevchooser is on the server end. Both sides have pulseaudio working fine.

Without firewall, everything works fine. With firewall, padevchooser can't see my thin client.

Completely opened port 4713 in firestarter. Applied. No go. Restarted pulseaudio on both ends, restarted padevchooser, no go. Rebooted both ends, no go. Firestarter shows no blocked connection attempts.

Stopped firewall, restarted pulseaudio/padevchooser, all is fine.

What could be causing this? Is there activity other than on p4713 which needs to be let through?

---

### Post by Defrector on 2009-05-03
I am so bumping this shizznit.

---

