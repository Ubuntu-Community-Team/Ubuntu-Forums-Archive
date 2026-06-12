---
title: "Atheros wireless and Ubuntu 8.10"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by penncon on 2009-03-06
I've had my wireless card working for a long time in 8.04 using the madwifi driver.  I upgraded to 8.10 last night knowing that installing the new kernel would cause me to lose my wireless.  However, now I can't get it to work at all.  I can't reinstall madwifi because 'make' returns an error that I need to enable wireless extensions.  I'm told that this is usually a mismatch in my kernel version and the headers that I'm using, but the headers and kernel match.

I've installed the restricted modules from the repository...no dice.

ath_pci gets loaded, my wireless card shows up in 'lspci' but the ath0 device never gets created.

Anyone have any ideas???  I'm going crazy here...

---

### Post by N04h on 2009-03-06
Can we get an ifconfig and iwconfig output?

---

### Post by RedSingularity on 2009-03-07
Did you try the ath5k or the ath9k drivers?  Thats how i have my atheros wireless working in intrepid.

---

### Post by kevdog on 2009-03-07
If you could post lspci -nnm it would be great.  Also lshw -C network might also provide help.

---

