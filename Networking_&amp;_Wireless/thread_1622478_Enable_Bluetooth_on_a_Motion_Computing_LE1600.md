---
title: "Enable Bluetooth on a Motion Computing LE1600"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by h38thsc0tt on 2010-11-15
I have been running 10.10 on my LE1600 for quit a while now. I have not been able to get the embedded Bluetooth adapter to turn on. I'm guessing it is a software switch somewhere that needs to be enabled.
 
Any ideas would be much appreciated.

---

### Post by roland-orre on 2012-04-18
> **h38thsc0tt said:**
> I have been running 10.10 on my LE1600 for quit a while now. I have not been able to get the embedded Bluetooth adapter to turn on. I'm guessing it is a software switch somewhere that needs to be enabled.
 
Any ideas would be much appreciated.

I have an LE1700 which has the same internal BT interface (Cambridge Silicon     Radion BC417
    which should work fine in Linux (if it was enabled...) the vendor/product id     is 10ab:1005 ) and I have the same problem. I wrote to Motion Computing technical support yesterday, but the answer was the expected. They can't help me as Linux is not supported on the machine... and it seems as not even the technical support have access to documentaion about what hardware registers need to be set.

I also replaced the WLAN card (mini pci-e) with an Intel N-6230 ABGN card which has bluetooth as well. The WLAN works fine (iwlwifi) but no BT. I assume the BT on N-6230 is through USB (pin 36,38 on mini-pci-e) which have bus connectors on the card, but either the WLAN slot has no USB or this USB is disabled as well. At the moment running with a Trust BT USB dongle  BCM2046B1alternatively with a 3com BT PCMCIA card which both works fine.

If this wasn't my main UI machine at the moment I would open it and find out hw-wise how to enable BT as it is a separate card. Alternatively try to disassemble the Motion Dashboard under Windows to see if their big secret can be revealed.

For my own I have no understanding at all why computer manufacturer should have these secrets. I can't see what extra benefits they can get by keeping such things secret... It was similar with an earlier tablet (Toshiba Portégé M200 also an excellent machine) but there Toshiba never revealed any doc about the SD-card reader so that was useless but the rest worked fine. Everything else works fine on this LE1700 though, I can get all the buttons working. The "Function" and the "Dashboard" buttons can be reached by
setkeycodes e079 <keycode>
setkeycodes e074 <keycode>

---

