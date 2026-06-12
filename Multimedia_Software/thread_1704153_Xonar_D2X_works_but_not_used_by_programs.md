---
title: "Xonar D2X works but not used by programs"
date: 2011-03-10
forum: Multimedia Software
---

### Post by H4rm0ny on 2011-03-10
Hi,

I just bought a Xonar D2X. Wonderful thing - recording from mic and quality of output to speakers is superb... on my Windows install. : /

It appears to work correctly in Kubuntu 10.10 as when I open up Sound and Video configuration, I can see it listed correctly and when I hit "Test", I get the annoying Ubuntu tinkle-plonk. But no application I use seems willing to use it. In fact, both Optical Outs (the motherboard's and the soundcards) are working fine when I try playing a test sound from this panel, but neither seems to be output to by VLC, Spotify or anything else I've tried.

I have set the entry "Xonar D2X Multichannel (IEC958 (S/PDIF)) Digital Audio Output to the preferred option for all output. Silence.

How do I convince VLC, Spotify et al, that the card really is there and they're really, really welcome to use it?

Thanks a lot,

H

---

### Post by H4rm0ny on 2011-03-10
Just in case any of this is relevant, the motherboard is an Asus M4A79XTD EVO. I have both the onboard and the soundcard's S/PDIF outputs hooked up simultaneously and - as stated - they both seem to work happily when I hit "Test" on them and the Sound and Video configuration panel says that the backend is "Xine".

---

### Post by H4rm0ny on 2011-03-10
Well I've gone done solved it myself, sorry folks. :)

For future reference, despite everything in KDE saying everything was fine and playing test boops, et al. When I typed alsamixer at the command line, it showed "S/PDIF" as Muted. I hit the 'M' key and Aretha Franklin was in my living room!

Thanks anyway,

H

---

