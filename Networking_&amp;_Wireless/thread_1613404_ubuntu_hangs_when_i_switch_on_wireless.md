---
title: "ubuntu hangs when i switch on wireless"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by rammbhat on 2010-11-04
Hey guys

Im using ubuntu on my hcl netbook.. (normal verson not netbook version) Ive freshly installed ubuntuu on this system..Everytime I switch on wireless lan using the function+f11 keys ubuntu hangs.. This doesnt happen with the other shortcut keys.. Pls help me out..
The netbook has realtek wireles lan device..

PS: shifting over to ubuntu netbook edition is not an option

---

### Post by grahammechanical on 2010-11-05
Are you not supposed to switch on wireless before you boot? The Linux Operating System loads various modules at boot time as it detects the hardware devices in the machine. It is not detecting a wireless hardware device, so it is not loading a wireless module. Then you switch on the hardware device and the Operating System hangs because it does not have the software module loaded for using this device.

This is my guess. I of course could be wrong.

Regards.

---

