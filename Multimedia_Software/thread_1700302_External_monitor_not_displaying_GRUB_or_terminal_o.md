---
title: "External monitor not displaying GRUB or terminal output"
date: 2011-03-04
forum: Multimedia Software
---

### Post by X-Legs on 2011-03-04
I am running Ubuntu 10.10 on a headless Macbook Pro. The screen is broken, so I use it as a desktop running on an external monitor. It has a 512 MB GeForce 8600M GT video card using the proprietary Nvidia drivers. At first, when installing the driver, I needed to modify xorg.conf to force the display to the external monitor. 

This works well for the most part, but the preload sequence (everything after EFI and before the desktop including GRUB) seems to be outputting to the broken laptop screen (the Apple logo lights up) and not to external monitor. The same thing happens when I use Ctrl + Alt + F4.

Is there anyway to force all of that to my external monitor too? I mainly want to be able to see GRUB, but having the terminal visible would be useful too.

Thanks   
X-Legs

---

### Post by swiftdr on 2011-03-30
I would like an answer to this too. I'm running on an old laptop whose backlight burned out so I have an external monitor set up. I have keep hitting the key combo to switch video to the external monitor to see GRUB at boot.

---

### Post by X-Legs on 2011-03-30
Mine is a Mac so it doesn't even have such a key combo. I also want to keep the laptop neatly folded away.

---

