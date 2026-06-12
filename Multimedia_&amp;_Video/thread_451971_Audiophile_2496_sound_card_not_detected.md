---
title: "Audiophile 2496 sound card not detected"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by Sabru on 2007-05-22
I have just installed a shiny new M-Audio Audiophile 2496 PCI sound card. 

Trouble is, not only am I not getting any output, but the device is not being recognized at all. Does not show up in volume control panel. Or in any audio program.

After disabling the integrated sound on the motherboard to isolate the problem, no audio device of any kind is recognized. (I get the little X next to the volume icon, etc.)

I ran lspci in the terminal, and it does seem as though the card is physically installed properly, if not configured properly.

```

02:02.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev ff) (prog-if ff)
        !!! Unknown header type 7f
```

okay, so the card is *there*, but that's about it. ice1712 is indeed supported by alsa, I checked. But why won't it recognize this card?

I am running Ubuntu Studio, if that helps. Any advice is appreciated.

---

