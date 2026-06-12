---
title: "recomendation wanted for video card  hdmi nvidia with sound"
date: 2011-07-25
forum: Mythbuntu
---

### Post by jeremycobert on 2011-07-25
does anyone have a recomendation for a pci express video card with HDMI and sound that works through the HDMI with mythbuntu and VDPAU that works.

i have a GTS-250 with HDMI, but it looks like the audio will not work on this card.

---

### Post by nickrout on 2011-07-25
What makes you think the 250 doesn't work? It should. What version of mythtv?

---

### Post by David Grigor on 2011-07-27
I have dedicated mythtv frontends ( 5 total ) all use GT220 or the newer version GT520.  All work out of the box with full vdpau on 11.04. I can't think of any reason to use a higher end card unless your also running windows and gaming on it.

---

### Post by declanmullen on 2011-07-30
> **jeremycobert said:**
> does anyone have a recomendation for a pci express video card with HDMI and sound that works through the HDMI with mythbuntu and VDPAU that works.

i have a GTS-250 with HDMI, but it looks like the audio will not work on this card.

Gigabyte GT430 [GV-N430OC-1GI]("http://www.gigabyte.com/products/product-page.aspx?pid=3629#ov") works fine with Mythbuntu 10.10 x86 32bit with its proprietary nVidia drivers. 

GT430 based cards like this one support a lot of the current VDPAU spec compared to many of the older nVidia chipsets. My Mythtv software is configured to use VDPAU and it seems to be working fine. 

Getting sound thru the card's nVidia HDMI requires some configuration, see  [posts 63 and 64]("http://ubuntuforums.org/showthread.php?p=10844182#post10844182") in the "[HOWTO: Ubuntu 10.10 Nvidia hdmi audio]("http://ubuntuforums.org/showthread.php?t=1668737")" thread. 

Like most GT430 cards it is thicker than a single slot and so may prevent you using the slot next to it. 

I've found its big fan to be quiet. However I only use the system for mythtv and web browsing, I don't use the system for gaming so the card (and its fan) is probably not being pushed very hard. 

Apart from the subject of noise levels, I believe that most nVidia GT430 based cards work just as well as this GV-N430OC-1GI. So you might experience similar levels of compatibility with any GT430 based card.

BTW, the info in the "[HOWTO: Ubuntu 10.10 Nvidia hdmi audio]("http://ubuntuforums.org/showthread.php?t=1668737")" thread might enable you to get your nVidia GTS-250 HDMI's audio to work.

---

