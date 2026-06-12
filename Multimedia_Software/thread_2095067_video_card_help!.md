---
title: "video card help!"
date: 2012-12-15
forum: Multimedia Software
---

### Post by Fozz on 2012-12-15
I have GV-NX62128dp video card that I'd like to put in my primary system.  An hp Pavillion a1340n The old GV-R38128 died and I'm now using the on board chipset. Sorry for asking for help  but I haven't been able to figure out  any of the info I've found so far and I'd like to get this thing in and off my never ending list of stuff to do!
the monitor is a 19' acer LCD and when I put the card in I get nothing from it and the system seems to stay on the on board chipset  I'm (obviously) not very good with  Linux but I refuse give up and go back to windows if someone can help or point me in a good direction I'd be grateful!  

12.04

 Thanks!!   Fozz

---

### Post by cwsnyder on 2012-12-15
What you are describing seems to not be a Linux problem, but a BIOS setting.

If you put the card in, but the boot screen with the HP logo telling you how to go into BIOS setup does not come up through your new card, then, with the monitor connected to the on-board video output, re-boot your computer to get to the HP logo screen where it tells you to press F2 ( or Del, or F1 or something else) to go to Setup and press the key it tells you to press before the screen goes away.

Be careful of what you set here, as it can cause you problems, but you need to find the section where you can disable the on-board graphics card.  When you do this, save and restart your computer.  No display should now come from your on-board graphics output, but display should show from your add-in card.

---

### Post by Fozz on 2012-12-15
Looked in the BIOS and found a vid card setting (on board, PCI' or PCI E)(THANKS!) However it didn't change, with the card in the PCI E slot I get nothing and even the onboard does not come up unless I remove the Video card completely :( card is new (though its been setting here a year almost) any other suggestions?

---

### Post by Fozz on 2012-12-21
Still hoping for a solution!

---

### Post by BicyclerBoy on 2012-12-21
Don't get upset by this question..

You do have the video cable removed from mobo jack & attached to the discrete video card?

Can you clarify what you mean by "come-up" ?:
- does BIOS boot splash show on discrete video card?
- does grub boot screen show up
- does ubuntu greeter/login screen show up

When you select onboard/mobo graphics (BIOS) at which point in boot process does it stop?
Does the BIOS boot show up?

Some mobo chipsets do not allow both cards to be used at same time.
This should not prevent you choosing one in BIOS...

FYI
This obscure descriptor "GV-NX62128dp" is an old nVidia 6200, must be one of the first PCIe ever made..

---

### Post by Fozz on 2012-12-25
1. Yes Monitor cable is switched from MB to video card output (That's a reasonable question given that you have no idea of my abilities)

2. All I get is a blank screen, no Bios screen, no grub no login.

---

### Post by Yellow Pasque on 2012-12-25
So you know the monitor is good, you've reseated the card in the mobo (firmly), and you changed the BIOS to boot PCIe first? If you still can't even get a BIOS screen, it's probably a bad card. I don't see any BIOS update for your system on hp's site, either.

---

