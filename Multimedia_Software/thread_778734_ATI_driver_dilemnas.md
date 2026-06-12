---
title: "ATI driver dilemnas"
date: 2008-05-02
forum: Multimedia Software
---

### Post by djmoore85 on 2008-05-02
Hey yall, have a few questions here. Alright, I have used envy to get my ATI driver to work. When I use the closest version it offers me of the driver for manual install, I can use advanced effects on the desktop, however my screensavers are choppy and sometimes freeze up. Now I reset everything to a fresh install for the video card using 

```
dpkg-reconfigure -phigh xserver-xorg
```

And now my screensavers run smooth, but no desktop effects. Also, a simple game like Supertuxcart freezes up and has jacked up graphics. However, using Envy, the game ran smooth. So I decided to try and install and use the ATI driver from their website, but can't get it to install. I used the instructions in the sticky at the top of this section and it hasn't worked yet. Kinda stuck here on where to go to get a nice balance for smooth screensavers, smooth gameplay and mild desktop effects. Here is info on my video card

```
 01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
```

Any other info yall may need to help get the drivers installed just let me know. Thanks in advance

---

### Post by Bablefish on 2008-05-02
If your computer has a 64bit CPU just head on over to the ATI site, they have Linux drivers ready for download.

---

### Post by djmoore85 on 2008-05-02
It's just a laptop with a AMD Sempron so I doubt it is 64-bit. I am having trouble installing the driver I downloaded from ATI's website, instructions from their site and the instructions from Ubuntu support are not working. Anyone happen to know what to punch in to check if it's a 64-bit processor?

---

### Post by robotcontrolledbiodomes on 2008-05-02
Yep, just open up the terminal and type in 'getconf LONG_BIT'. Or you could also type in 'uname -m'

---

### Post by djmoore85 on 2008-05-02
Appreciate it man, I found somewhat of a middle ground. I downloaded the driver for my card from ATI's website and decided to run Envy in automatic rather than manual, and in reading the envy terminal as it installed it said it found ATI driver installer, so maybe it installed the one I downloaded. I can't turn any effects on whatsoever or it screws up the display and causes flashing and what appears to be bad refreshing going on. So until I build a replacement computer I'll settle for the setup and what works now. Unless anyone has any suggestions on where to go from here I think I'll just keep it how it is

---

