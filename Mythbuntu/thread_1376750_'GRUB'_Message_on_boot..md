---
title: "'GRUB' Message on boot."
date: 2010-01-09
forum: Mythbuntu
---

### Post by patdaman45 on 2010-01-09
I'm new to linux, and after a couple successful Ubuntu installs i thought i'd try Mythbuntu.  After installing the OS, i got to the setup menu, after completing the setup of my tuners, it prompted me to restart the computer, after the restart the boot will hang at the message 'GRUB'.

Specs:
Processor AMD Athlon X2
Memory 2gb ddr2 800
HDD
    1.320 GB
    2.2tb
Disto used "mythbuntu-9.10-desktop-i386.iso"

Any help would be very helpful.  Thanks!

---

### Post by jeffwiggins on 2010-01-09
It sounds like your system is not finding the bootable filesystem to proceed.  do you see menu selections?  Depending on your version of grub you can use either 
"esc" or the tab key sometimes to display the options.

try booting off your install cd and checking your grub configuration file and run a grub update so that it rereads the grub.conf file.

Jeff.

---

