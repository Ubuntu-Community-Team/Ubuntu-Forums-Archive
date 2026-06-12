---
title: "PCI nVidia card woes"
date: 2006-01-19
forum: Multimedia &amp; Video
---

### Post by mzuverink on 2006-01-19
How can I install install a pci nVidia card to a system that has already been configure to use the onboard Intel graphics chipset.

Here is the background:
I switched from Mandriva to Ubuntu.

The nVidia card has always been in the machine since I installed it since I cought the machine.

The nVidia card is a gForce MX-400

Mandriva(Mandrake) has always detected the card an configured XORG to use the "nv" drivers without any user interaction(for the most part).

When attempting to install Ubuntu the installation froze and would not continue or complete at the stage where it detects hardware and configures XORG.  I had a black screen with a non-blinking cursor.  I attempted to reboot and it went straight to a root prompt.  The system had not completely installed and I could get none of the tools to even check XORG.CONF 

I tried installation several times and figured it was the card and removed it.  I reinstalled and it the installer finished properly.  I have been using the Intel graphics chipset for three weeks, but am unable to do my normal usage due to its graphic limitations.

I would like to now add the nVidia card, reconfigure XORG to use it but am unsure of how to do so.

In Mandriva if I would attempt this it would detect new hardware and prompt me for action.  Ubuntu does not do this, nor does it detect the hardware.  X will not start with the card in since it is not configured to use it.  I cannot even get to a shell to run the tools to do so.

The version of Ubuntu that I am using is 5.10.

Any assistance would be greatly appreciated.

Thanks

---

### Post by Elvish Legion on 2006-01-20
Make sure onboard video is disabled in the BIOS

---

