---
title: "System not recognizing Evga 8800 GTS"
date: 2009-08-20
forum: Multimedia Software
---

### Post by Cr4shJunkie on 2009-08-20
I'm  trying to install a new video card and I don't think the system is recognizing it.

I attached the card to the motherboard, connected the PSU to it, turned on the computer to use the command below:

```
sudo apt-get install nvidia-glx-new
```Then I rebooted with the monitor plugged into the card and got the "signal not found, check cable" message on the screen.

As in the title, the card is an evga 8800 GTS.  I use Ubuntu 8.04 Hardy Heron.  Please let me know if any other info is needed.  Thanks in advance for any help.

-angelique

---

### Post by dagrump on 2009-08-20
Were you using on-board video before installing this card?
If you were you would need to alter your BIOS to use this & not the on_board chip.
Or it is possible the card isn't seated just so, & is being a pain.

---

