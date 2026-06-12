---
title: "natty: lirc_serial irblaster and myth"
date: 2011-06-04
forum: Multimedia Software
---

### Post by astrand on 2011-06-04
Hi All,
I'm trying to get an irblaster to control a directtv H20 STB.  My computer has no built in serial ports so I have installed a pci serial expansion board.  The kernel recognizes two ports, /dev/ttyS4 and /dev/ttyS5.  My irblaster also has an indicator led so I can see if any signal is going to it.  If I echo a character and redirect it to /dev/ttyS4 (the IR blaster is attached to this one) the blaster definitely glows red so the wiring seems ok.  Also this same blaster used to work with the same board under 9.04 (HD failure forced an upgrade)

I think my problem is that I cannot seem to configure lirc_serial.ko to recognize ports other than ttyS0 or ttyS1.  I modified /usr/src/lirc-0.8.7/lirc-modules-source.conf to reflect the correct irq (16) and port (0xdc00) for ttyS4.  dpkg-reconfigure seems to rebuild the module and throws no errors, but the blaster still does not light up.  modinfo lirc_serial also reports the same irq (3 or 4) and port as it does under a clean install of lirc-modules-source without my mods.  As a result I think that there's a problem with lirc_serial config.  

BTW I have tried setserial /dev/ttyS4 uart none before using the blaster.  Also this is a stock 11.04 install, not mythbuntu

Any ideas?
Thanks,
Allan

---

