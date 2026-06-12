---
title: "Help needed configuring ISA soundcard"
date: 2008-07-30
forum: Multimedia Software
---

### Post by ossinthedesert on 2008-07-30
Hello, all.

I've recently installed Xubuntu 8.04 onto my desktop. Everything's great, except that there's no sound, and I need to configure my 8 button mouse (but I can fix that later). My sound card is an old, Creative Soundblaster 16 ISA. I've followed the instructions laid out in the Comprehensive Sound Problem Guide, but I got nowhere. 

Any help is appreciated, thanks in advance.

---

### Post by yldouright on 2009-05-21
You probably got this sorted out already but in the event you didn't, here is what I do to configure ISA cards manually:

1. Get the port I/O, IRQ and DMA information on your card from either the Windows OS device manager or your bios and write them down for reference.
2. Set your PnP OS bios setting to NO if you have it.
3. Make sure your cards are not in conflicting slots. Many motherboards share an IRQ for PCI slots (Asus will typically share the AGP with its adjacent pci slot 1, slot 3/6 and slot 4/5 are other common sharing pairs.
4. Add your ALSA module to the /etc/modules file and reboot. After the reboot go to the System>Preferences>Sound menu and change the "AutoDetect" settings to ALSA. If the card is still not working you will need to add the configuration information from step 1 along with isapnp=0.
5. That should get you fixed.

---

