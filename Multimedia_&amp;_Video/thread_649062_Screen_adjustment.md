---
title: "Screen adjustment"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by punkrockguy318 on 2007-12-24
Hello.  I'm using Ubuntu on my Sceptre X23 monitor.  It works well with the nvidia driver and all, but my screen is lightly offcentered to the left.  My monitor has no controls for fine tuning the picture like that.  I'm ocnnectred through VGA
 Is there some way I can adjust it through the software?  Thanks

---

### Post by taurus on 2007-12-24
See if you can shift your screen around with

Applications -> Accessories -> Terminal
```
gksudo nvidia-settings
```

---

### Post by punkrockguy318 on 2007-12-24
i don't see an option for it in there

---

### Post by Craigus on 2007-12-24
From here: [http://www.sceptre.com/Products/LCD/Specifications/spec_x23sNaga.htm]("http://www.sceptre.com/Products/LCD/Specifications/spec_x23sNaga.htm")

> User Controls 
Power On / Off, OSD, Contrast, Brightness, Audio Volumn, Auto Adjust, Scale, Clock, Phase,[COLOR="Red"] H-position [/COLOR], V-position, OSD H-position, OSD V-position, Language, Information, Reset, Color Temperature, 9300ºK, 6500ºK or user defined.

Are you sure you can't adjust the horizontal position via the built in menu ?

---

### Post by punkrockguy318 on 2007-12-24
Wow, there was an option for that.  Thank god I was going to be a little worried if there wasn't .  Thank you were very much .  It was sort of hidden in the menus.

But by the way, I've read of other people having problems with this offcentered behavior on their TVs.  Is there anyway to do screen adjustment through X?

But mine is working fine now, thank you.

---

### Post by cgm12mgc on 2007-12-26
my screen is doing something similiar, its all off to the left, iv got the H position scrolled to the right 100 percent, theres a blue line on the right with a black space about an inch wide,    anyone have a solution for this?

Thanks,
Charlie



--edit-- it changes from left to right when i change my res from 1680x1050 to 1280x1024 so its got something to do with that.. got me stumped

---

