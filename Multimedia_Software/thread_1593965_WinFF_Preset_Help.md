---
title: "WinFF Preset Help"
date: 2010-10-11
forum: Multimedia Software
---

### Post by Sum Guy on 2010-10-11
I've been using WinFF for a while, but I've been having a bit of a problem. For some reason, when I edit the bitrate for a preset, nothing changes. For instance, I tried setting the bitrate in the super high quality MPEG 4 preset to 3000kbits/s, and the encoder insists on running at 7000, which is providing no gain in quality at the cost of a file more than twice as big. The problem appears to be somewhere in the preset, as the terminal doesn't appear to register the new bitrate. Anyone know what to do?

---

### Post by andrew.46 on 2010-10-12
Hi Sum Guy,

Are you modifying $HOME/.winff/presets.xml? If so could you post the changes reflected in this file...

Andrew

---

### Post by Sum Guy on 2010-10-13
No, I've been using the preset editor in the program. Does it matter?

Thanks

---

### Post by andrew.46 on 2010-10-13
Hi,

Should accomplish the same end. Can you attach your $HOME/.winff/presets.xml to a post? This will demonstrate definitively what the preset is doing, I suspect that if you are using the gui to modify the preset you may have not pressed the button: 'Add / Update' which gives a confirmation dialogue to modify the preset.

Andrew

---

