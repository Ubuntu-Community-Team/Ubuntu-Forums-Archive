---
title: "resolution issues"
date: 2008-06-26
forum: Multimedia Software
---

### Post by Graffight on 2008-06-26
Ok so I'm ridiculously new at this...question...any time i put my resolution up any higher than default the screen gets all...wiggy (for lack of better terms). there the screen splits up into multiple mirrors of itself. is this a video card problem and i just need to figure out how to install the drivers, or is it something else?

---

### Post by kagashe on 2008-06-27
> **Graffight said:**
> Ok so I'm ridiculously new at this...question...any time i put my resolution up any higher than default the screen gets all...wiggy (for lack of better terms). there the screen splits up into multiple mirrors of itself. is this a video card problem and i just need to figure out how to install the drivers, or is it something else?To know the video card type following in terminal:
> lspci | grep VGA

To know about resolutions type following in terminal:
> xrandr -q

You can paste the output of these commands here.

kagashe

---

### Post by Graffight on 2008-06-28
thanks for the info...i upgraded to Hardy and the problem was solved

---

