---
title: "orinoco_pci driver locks up system with: error -110 writing Tx descriptor to BAP"
date: 2010-08-05
forum: Networking &amp; Wireless
---

### Post by huzzam on 2010-08-05
Hi--

I'm running 10.04.1 (kernel 2.6.32-24-generic #38-Ubuntu i686) on an IBM Thinkpad T30. After my machine's been up for a short while (10-30 minutes), it becomes almost completely unresponsive, with user input (mouse movements, clicks, keypresses) taking over a minute to register. I switched to another TTY (with ctrl-alt-f4) and there's a constant stream of the following error:

```

[ 1234.567890] eth1: Error -110 writing Tx descriptor to BAP

```

Aside from the number at the beginning, it's the same error over & over (specifically, I get 10 more every 5 seconds).

My wifi card (which is eth1) is an "Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)," with firmware "Intersil 1.4.9," and it's running under the orinoco_pci driver, version 0.15.

**How can I fix this & get a usable system?** As it is I have to force reboot (via the power switch) every half hour or so, losing all my work!

Obviously the system is basically useless like this, so any help would be greatly appreciated!

Thanks
~peter in Oakland

---

