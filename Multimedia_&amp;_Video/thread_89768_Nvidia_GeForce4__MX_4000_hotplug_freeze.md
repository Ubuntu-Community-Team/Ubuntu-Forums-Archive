---
title: "Nvidia GeForce4  MX 4000 hotplug freeze"
date: 2005-11-13
forum: Multimedia &amp; Video
---

### Post by Tuxtur on 2005-11-13
Trying to install ver 5.10. The PC freezes at "Starting hotplug subsystem"
I'm using a Dell 2350 which has onboard video. I have the onboard video turned off in the bios. It has an Nvidia GeForce4 Mx4000 PCI card installed.

Troubleshooting this I discovered that if I turn the onboard video back on in the bios, plug my monitor into that port and leave the Nvidia card in its PCI slot the system boots.

The onboard video stinks so I'm not giving up my Nvidia card. Any ideas as to how I can get the system to boot with the Nvidia card?

---

### Post by Teroedni on 2005-11-13
can you see in bios if ther is an option to choose between agp and pci.
If there is choose pci

---

### Post by Tuxtur on 2005-11-13
Teroedni - The only option in the bios is "on" or "auto" with the auto being the one that shuts off the onboard video.

---

### Post by Teroedni on 2005-11-13
could you state which motherboard you use?

---

### Post by Tuxtur on 2005-11-13
Re: Motherboard
Ran Belarc Advisor in Windows XP and got the following results
Main Circuit Board
Board: Dell Computer Corporation
Bus Clock: 400 megahertz
BIOS: Mitac International A02 03/24/2003

---

### Post by Teroedni on 2005-11-13
can you set pnp=no in bios?

---

### Post by Tuxtur on 2005-11-13
Just checked Dells site and I already have the most recent Bios ver A02.

The Bios does not have PNP option of any kind

---

