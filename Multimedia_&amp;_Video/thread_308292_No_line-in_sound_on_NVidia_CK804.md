---
title: "No line-in sound on NVidia CK804"
date: 2006-11-27
forum: Multimedia &amp; Video
---

### Post by chrono325 on 2006-11-27
Hey all.

I am attempting to get the line in to work on my integrated sound card so I can play my shiny new Wii on my computer. Video input already works fine, thanks to a cheap bttv card, but since the card has no sound input of its own, I have to use something else. I got an RCA to minijack adapter from Radio Shack, so I can plug the output of the Wii into the line in on the back of my compy, but the problem is that doing so generates no sound to speak of.

Playing sound works fine, the mic plays sound over the speakers, but no luck with line in. I went into alsamixer and unmuted the Line input, set it to a reasonable volume, and selected it for capture. Nothing.

Here is some info about the chip from alsamixer:
Card: NVidia CK804                                                          
Chip: Realtek ALC850 rev 0

it seems that it is using the snd_intel8x0 module, since that one is loaded.

I also have a Sound Blaster MP3+ which is a USB sound card (and works surprisingly well in fact). It is cool enough to have RCA line in ports right on the thing, and works perfectly fine. I would like to be able to use the onboard card since it is already connected to the speakers and doesn't require another box lying around.

Any ideas about what might be wrong?

---

