---
title: "Multiple Display setup - multiple cards - Possible?"
date: 2008-03-09
forum: Multimedia &amp; Video
---

### Post by bkortleven on 2008-03-09
I was just wondering...

Is it possible to put in more than one Graphics card in a computer... Yes...

Combination AGP/PCI and PCI-express/PCI works...

BUT:


if you have a motherboard with 2 (or even 4 as some of the abit boards seem to have) PCI-express x16 slots, can you fit 2 or 4 graphics cards in it?
How will X respond? Can you use the graphics cards independently (hooking up 4 or even 8 monitors) or can you only do a SLI- or Crossfire-like configuration?

I ask this question because I'm looking for an easy, cheap way to make a Distributed X server, to have a very large display/video wall setup for a show... and Linux looks like the best option to do it myself, instead of spending € x0000,00 on a setup that uses LED tiles with a minimalistic resolution like 400x400 pixels per 50cmx50cm...
If I can use like 4 machines, hooking up 16 or even 32 displays, using 'cheap' 4:3 19" TFT monitors, I could make a huuuuuge videowall... and do it myself... Even putting some old ATI 9600 PCI cards next to it, it could be possible with 2 backend X machines..., no?

Is there anyone here that has an SLI or X-fire board, hosting 2 or more display cards, that can do a multi-display setup, using the cards independently?
If so, can you post a lspci or so, so I can how the PCI (express) bus behaves...
and, if possible and used in multi-monitor mode, an xorg.conf file mentioning 4 displays or more?

If I'm wrong in my thoughts here, let me know... I'm just checking, before buying the equipment...

Thanks!

Bram

---

### Post by kidders on 2008-03-10
Hi there,

What you're describing is possible in theory, but I have a few practical concerns ... maybe some other posters might be able to confirm or discount them.

**- I -**
While I've never done anything even *close* to the scale you're talking about (4 cards & 8 monitors per box, and the like), I have noticed that multi-card and multi-monitor setups can get a bit sluggish when Xorg is pushed really hard. You'll probably have to ...[LIST]
[*]Be very careful about the hardware you choose. You'll need to carefully pick cards with _very_ good Linux support.
[*]Experiment with different versions of Xorg, and play with building it differently, to see if you can optimise it for purpose as tightly as possible.[/LIST]I may be wrong, but I suspect your X server will just fall over if you don't get the basics exactly right. No doubt you'll want your video wall to do some pretty demanding things. :-P

**- II -**
I'm not sure Ubuntu is the quite the right distro for a job like this. If it were me, I would go with something designed to be flexible rather than easy to use, and optimise the hell out of it ... gut the kernel, and tweak Xorg to within an inch of its life.


I'd recommend visiting Xorg's forums ... there are bound to be people there who know *exactly* what they're talking about. They may be able to answer questions like whether you should go out of your way to use a multi-core CPU for better performance, how much RAM you're likely to need, and so on.

---

