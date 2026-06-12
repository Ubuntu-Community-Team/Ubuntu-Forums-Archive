---
title: "*HELP* - Using an IguanaWorks USB IR Transceiver for Changing Channels?"
date: 2007-12-20
forum: Mythbuntu
---

### Post by obscure411 on 2007-12-20
OK, so I've had Mythbuntu 7.10 x64 running for over a month without any issues.  Everything seems to work just fine, but the new hardware I'm using has no serial ports on the motherboard, so the existing Serial IR Blaster I was using will no longer work.

Because of this, I bought an IguanaWorks USB IR Transceiver ([http://iguanaworks.net/product1.psp](http://iguanaworks.net/product1.psp)) as it seemed to do exactly what I wanted - even controlling two separate cable boxes with only one transceiver... sweet!

So I install the latest .deb file from their website, the daemon starts just fine and I see the appropriate /dev/iguanaIR mappings appear.

So why is it that no irsend commands work?  According to the IguanaWorks website I need to use the irsend command twice, but I'm not getting any output and the channels still aren't changing even after the second irsend command.

Any advice?

---

### Post by OffAxis on 2007-12-20
have you set up your set top boxes correctly in lircd.conf?

what does 
```
sudo irsend LIST "" ""
```
give you?

---

### Post by RickThorpe2006 on 2007-12-28
I had problems getting this device running as well.  What worked for me was (a) doing a complete uninstall of lirc, and then compiling from the current cvs (linked at the lirc.org site), (b) running /etc/init.d/lirc stop as root, and (c) running lircd as root (you can add steps b and c to your /etc/rc.local, but will want to add a sleep command before each line).

---

