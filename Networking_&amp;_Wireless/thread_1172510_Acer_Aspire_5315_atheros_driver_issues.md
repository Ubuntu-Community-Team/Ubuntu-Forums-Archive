---
title: "Acer Aspire 5315 atheros driver issues"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by NMbottlecap on 2009-05-28
I just installed 9.04 on my system, (clean install, no more Amiga OS for me). Anyway I had the wifi working without a problem, I was using the madwifi driver and then I restarted it and now I can't get the wifi working, the madwifi driver says it's activated and currently in use.  when I try ifconfig it doesn't even show an eth1 just eth0 and lo

---

### Post by t0mppa on 2009-05-28
Madwifi shouldn't show eth1 anyway, rather ath0 and wifi0.

Anyway, run **lshw -C network** from the terminal and see what it says about your wireless interface. Unclaimed means there are no drivers associated with it, if that's the case just try **sudo modprobe ath_pci** and see if that helps. Disabled means the interface is down, if so try **sudo ifconfig <logical_name> up** and see if that makes a difference.

---

### Post by NMbottlecap on 2009-05-28
> **t0mppa said:**
> Madwifi shouldn't show eth1 anyway, rather ath0 and wifi0.

Anyway, run **lshw -C network** from the terminal and see what it says about your wireless interface. Unclaimed means there are no drivers associated with it, if that's the case just try **sudo modprobe ath_pci** and see if that helps. Disabled means the interface is down, if so try **sudo ifconfig <logical_name> up** and see if that makes a difference.

Thanks for your help on.  I"m in this for the long haul.  I tried the commands you suggested my card is UNCLAIMED and so I ran the **sudo modprobe ath_pci** and that did nothing.  I disabled the madwifi to see if that would make a difference when I ran the **sudo modprobe ath_pci** and it didn't.

Next idea?

---

### Post by t0mppa on 2009-05-28
Ath_pci is the module for madwifi, so if you disable it, it surely won't work. :)

Anyhow, it was just a quick way to see if we could get it to work without too much trouble, but these things are rarely that simple.

Ok, let's do some further troubleshooting. Run **lspci** from the terminal and paste the line about your atheros card here to find out which chip type is giving trouble. Also, do a **lsmod | grep ath** to check if there are modules from multiple drivers loaded.

Did you just go for the madwifi straight off after installing or did you try the ath5k first, which comes as a default on 9.04?

---

### Post by NMbottlecap on 2009-05-29
Thanks for all your help.  I got frustrated so I reinstalled Jaunty, and stayed away from the madwifi driver, and now I am writing to you from my Acer on wifi and really enjoying it.

Thanks again for the help

Matt

---

