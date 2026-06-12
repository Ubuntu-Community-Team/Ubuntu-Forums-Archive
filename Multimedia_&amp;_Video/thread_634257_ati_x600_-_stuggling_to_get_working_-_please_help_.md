---
title: "ati x600 - stuggling to get working - please help me."
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by Sobiquet on 2007-12-07
Right here's the deal i've had ubuntu just over a week, and i love it but i really want to play games and get beryl working but this gfx problem is obviously preventing me from doing so,

I have and Ati x600 pci, a 3.4 ghz intel pentium 4 processor, and 1gb of ram.

I would really just love a simple explanation of what to do.
When i enable the drivers for my card in "restricted drivers"
my computer loads with "ubuntu" running in low grpahics mode and instead of ati in the gfx card list it is on vesa.:confused:

To get back to my resoloution of 1280-1024 I have to select back on the ati drivers in the list, and then when I reload my computer the card has been disabled again, this is really getting me down, on windows i have ran CS:S, WoW, COD 4, and many other games all with great performance.

This is my first test for this great ubuntu community :) make me happy oof my windows boycott because my only option left is mac!

thanks alot for reading, and helping.
sob.

---

### Post by JPWheless on 2007-12-07
I have the same problem with the same video card and similar computer specs.
I'm waiting for a reply too.

---

### Post by Sobiquet on 2007-12-11
bump?

---

### Post by Yellow Pasque on 2007-12-11
You should probably forget about Beryl. 3D Performance is terrible with fglrx. Nevertheless, go to System->Administration->Restricted Driver Manager and make sure the proprietary driver is enabled.

Then fire up a terminal and
```
sudo aticonfig --initial --overlay-type=Xv
```

Now reboot.

---

### Post by Sobiquet on 2007-12-31
that didn't do me any good i'm afraid, i'm still stuck here and i really do not want windows, any ideas anyone? and if so could you walk me through i'm a real newbie :/

thanks alot.
sob

---

