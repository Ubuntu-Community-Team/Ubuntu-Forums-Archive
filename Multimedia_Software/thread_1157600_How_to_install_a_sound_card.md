---
title: "How to install a sound card?"
date: 2009-05-12
forum: Multimedia Software
---

### Post by Cam42 on 2009-05-12
Okay, I picked up an old Monster Sound MX300, and I need to know how to install it.
I popped it in to the PCI slot, and got no sound, but the volume control went to the card and not my integrated sound.
Are there other cables I need to connect?
Is it a driver issue?
Is the card just broken?

---

### Post by Skripka on 2009-05-12
> **Cam42 said:**
> Okay, I picked up an old Monster Sound MX300, and I need to know how to install it.
I popped it in to the PCI slot, and got no sound, but the volume control went to the card and not my integrated sound.
Are there other cables I need to connect?
Is it a driver issue?
Is the card just broken?

Try reinstalling anything listed in Synaptic that has Alsa in the name....that should also reconfigure Also to talk to the new hardware...presuming that works, odds are you'll also have to reinstall your other media libraries to get them to recognize the new hardware addresses.

If you have an documentation, that would tell you about the hardware installation end of things.

---

### Post by Cam42 on 2009-05-12
Alsa or Also?

---

### Post by Skripka on 2009-05-12
> **Cam42 said:**
> Alsa or Also?

ALSA (meaning Advanced Linux Sound Architecture)

---

### Post by Cam42 on 2009-05-12
Okay, re-installed ALSA, but it's still not working.
but when I open Volume Control, I can chose between the sound card and my integrated sound.
Do I need to connect any cables to the card? Because all I did was put the card in the pci slot.
There are spots on the top of the card to plug something in, but I dunno.

---

### Post by lisati on 2009-05-12
> **Cam42 said:**
> There are spots on the top of the card to plug something in, but I dunno.
My best guess (without looking up your sound card) is that some of the slots could be for stuff like hooking it up to your CD/DVD drive. If that's the case I wouldn't worry about it too much at this stage.

---

### Post by Skripka on 2009-05-12
Okay, I did some digging....

This is the best lead I have found...

This page lists you card and chipset...this is a 10 year old card...

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Diamond_Multimedia](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Diamond_Multimedia)

To get it working, here is what is needed done:

[http://www.alsa-project.org/main/index.php/Matrix:Module-au8830](http://www.alsa-project.org/main/index.php/Matrix:Module-au8830)

---

### Post by Cam42 on 2009-05-12
Okay, Tried the instructions there, and when I get here
>   
       cp /downloads/alsa-* .

I get >   cp: cannot stat `/downloads/alsa-*': No such file or directory


---

