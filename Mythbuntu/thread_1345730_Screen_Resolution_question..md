---
title: "Screen Resolution question."
date: 2009-12-04
forum: Mythbuntu
---

### Post by Gamblor74 on 2009-12-04
Ok,

These may seem like silly question, but any advice help would be greatly received.

I have P4 3.2HT PC, running mythbuntu 9.10, with a WIN TV Nova PCI card. This is connected to a 23" TV via the VGA lead with a maximum resolution of 1680x1050. The desktop is currently set to this resolution.

Would my system performance, be better if I use a lower resolution (if so, what would be recommended). When selecting watch TV, does the resolution lower to the TV output, or does the system upscale (and therefore use more processing power) to show the picture?

I've notice a distinct difference in quality, between the TV’s digital quality (much better) and the Watch TV quality Via Mythbuntu...is this just down to my capture card hardware??

Again, 

Thanks for any help provided....

G-Man

---

### Post by blackoper on 2009-12-06
yes it's the capture card hardware that is the issue I would think. It's only capturing in analog

---

### Post by williammanda on 2009-12-06
Whenever you setup the digital tuner also checkout you video card as a last test for the whole senario.

---

### Post by nickrout on 2009-12-06
Make sure that the WinTV Nova is capturing at as close to possible native NTSC/PAL resolution. Usually NTSC -> 720x480 and PAL -> 720x576. Myth may have defaukted to something like 480x480

---

### Post by SiHa on 2009-12-07
Don't mean to sound daft, but doesn't 'Nova' indicate a DVB card? In which case the capture resolution bit is not relevant, the card does not do any encoding, just captures the broadcast MPEG stream. I assume it's a Nova-T/S?

I think you will find the difference in quality is due to the scaling, as you suggested.

However, it's going to be scaled whatever you do. Maybe you'd be better off playing with your playback profiles?

---

### Post by Gamblor74 on 2009-12-07
Yes It's a WinTV-NOVA-TD 500.

Dumb question number 2....Playback profiles??

---

### Post by SiHa on 2009-12-07
Under TV Settings -> Playback, page 2/3. The profiles set what hardware / software you use to decode the MPEG stream. Ranging from CPU-- to CPU++ each profile towards CPU++ uses a more processor-intensive method. Some will produce better results than others. 

The profile screens are initially a bit cryptic, but essentially, you have one or more entries, where a decoding method is set, dependant on resolution.

If you have a 8/9 series nVidia chipset (there are others, as well) you can use one of the VDPAU profiles to use the graphics hardware for the decoding. Some people, though, prefer the software route for picture quality (I'm not one of them!).

So you can try the different profiles, and also the different de-interlacers. To change the de-interlacer, you select one of the entries in the profile settings, and select 'Edit', on the second page of the options you can change the deinterlacer. I like to create a new profile (something like rez > 0,0 -> XVideo) and play with that, safe in the knowledge that I'm not going to bugger anything up.

Also, when watching a recording or live TV, if you press 'M', it brings up an onscreen menu. One of the options will change the display from interlaced to progressive, that may make a difference.

As far as your screen resolution goes, I'd say the 1680x1050 is pretty wrong. I don't know if you have a widescreen or 4:3 TV, but that resolution has an aspect ration of 1.6, which is neither 16:9 or 4:3. So your picture is being strectched one way to scale it to the desktop, and your TV is stretching it the other way to fit it back to the screen. For my widescreen, I use 1280x720. Let's face it, anything more than 576 horizontal lines is fairly pointless! (Even for the HD, as my TV is 720p)

---

### Post by Gamblor74 on 2009-12-07
SiHa, thanks for you help. Very useful information.

I will try this later tonight. My Video card is 8400GS so will play with the settings and see what I can do. It is a wide screen TV also.

Many thanks for the Help.

---

### Post by SiHa on 2009-12-07
Of course, I forgot one thing. It might just be that the VGA input on your TV is not good. TV manufacturers spend a lot of time optimizing HDMI, VGA is often an afterthought.

---

### Post by Gamblor74 on 2009-12-07
True,

It's an LG TV/Monitor and I have many DVD's and AVI files that I've played and the quatily on those are fine.

---

### Post by SiHa on 2009-12-07
If it has HDMI in, you could try a DVI-HDMI converter cable, you would probably get better results.

---

### Post by nickrout on 2009-12-07
> **SiHa said:**
> Don't mean to sound daft, but doesn't 'Nova' indicate a DVB card? In which case the capture resolution bit is not relevant, the card does not do any encoding, just captures the broadcast MPEG stream. I assume it's a Nova-T/S?

I think you will find the difference in quality is due to the scaling, as you suggested.

However, it's going to be scaled whatever you do. Maybe you'd be better off playing with your playback profiles?

you are right (after seeing the subsequent post). If the card had been described correctly in the first post I wouldn't have said what I did!

---

