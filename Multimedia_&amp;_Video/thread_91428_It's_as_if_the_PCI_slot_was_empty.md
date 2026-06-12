---
title: "It's as if the PCI slot was empty"
date: 2005-11-17
forum: Multimedia &amp; Video
---

### Post by Schiphol on 2005-11-17
Hello,

I've been using Ubuntu (as my first Linux experience) for about 7-8 months now, first Hoary and now Breezy. I am almost completely happy with it.

I say "almost", because the sound has never worked. I have a Speedio Novation USB soundcard but, being unable to make it work, I'm currently trying a Creative CT4810 PCI card. It's a very very simple card, so I was sure it would be straightforward for Ubuntu to recognize it. The thing is, it isn't. Not only the sound is not there, but the card itself seems to be missing. It does not appear in the Device Manager, and when I do "lspci | grep audio" I get NO result. lspci yields:

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8753 [P4X266 AGP] (rev 01)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:0c.0 USB Controller: NEC Corporation USB (rev 43)
0000:00:0c.1 USB Controller: NEC Corporation USB (rev 43)
0000:00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

Any idea what I can do to make Ubuntu recognize the card?

Thanks!
Manolo

---

### Post by az on 2005-11-17
Is it disabled in BIOS?

---

### Post by Schiphol on 2005-11-17
How can I tell?

Thanks for your help.

---

### Post by az on 2005-11-17
When you first turn on your computer, how to get into "setup" or "bios" or whatever is usually displayed.  It could be by pressing "del" or F2 or some other key.

Once in the BIOS or CMOS or Setup menu, look around for where you can determine your devices.  BIOS menus are all different, so it is hard to give ou step-by-step details.

---

### Post by Schiphol on 2005-11-17
I've been playing around with the PCI info in the setup menu. I have not been able to find detailed info about the peripherals in my computer. Anyway, I've been messing with a "sound card" flag and now lspci | grep audio answers:

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)

Is this the Creative soundcard?

Thanks,
M

---

