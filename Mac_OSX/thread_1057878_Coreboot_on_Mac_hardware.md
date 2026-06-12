---
title: "Coreboot on Mac hardware?"
date: 2009-02-02
forum: Mac OSX
---

### Post by DeadSuperHero on 2009-02-02
I know this isn't specifically about Mac OSX, but this pertains to Mac hardware. I figured it would go well here.
 
I'm personally thinking of getting a Mac, mainly because I'm thinking of starting up a Libre distribution as a hobby project. I figure if I can get great support on one platform of standardized hardware first, I can work my way towards a very stable and rounded-out laptop OS.
 
However, my main concern is EFI. It's proprietary, and I don't want that. I've been googling around, and haven't been able to find an answer for this so here goes:
 
I want to flash a Macbook/Macbook Pro's EFI and replace it with Coreboot (a.k.a LinuxBIOS). However, I haven't found any instructions on doing so, or even any comments about this being possible.
 
So my questions:
 
1.) Is this even possible right now? 
     a.) If so, how?
     b.) If not, how could one go about porting Coreboot to the mainboard on Mac hardware?
 
2.) How extendible is Coreboot currently. Can it run a simple XServer for a cairo-based loading screen, to smoothly transition into the GDM or KDM screen? 
 
3.) What pieces of hardware are there Free Drivers for, currently? (At least, for the latest Macbooks anyways).
 
4.) Which drivers need to be matured/written for it?
 
5.) Is Coreboot capable of ROM emulation to make one type of hardware run with the identification of a seperate brand, or emulate BIOS for other machines? This could be handy for anyone who wants to install a PC-specific OS, or just easily flash EFI back if they weren't happy with their experience.
 
In the meantime, I'll be reading up on documentation, but if anyone has advice upon the matter, please let me know!

---

### Post by mips on 2009-02-02
Just be carefull is all I could suggest as this has the potential of bricking your laptop.

If it's any consolation the EFI shell is open source if I'm not mistaken.

---

### Post by handy on 2009-02-02
I'd be talking to the Coreboot people as well before I took the risk of creating a very expensive brick.

---

