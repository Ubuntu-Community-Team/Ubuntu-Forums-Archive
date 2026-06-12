---
title: "No sound after Gutsy beta upgrade"
date: 2008-03-21
forum: Multimedia &amp; Video
---

### Post by fadastic on 2008-03-21
For some reason I'm not getting any sound, now. And when I try to open the volume control I get any error stating "No volume control GStreamer plugins and/or devices found."

---

### Post by Knowles on 2008-03-21
What's the card/chipset

try

lspci -v

and post back.

---

### Post by fadastic on 2008-03-21
I have a Sound Blaster Audigy 2 ZS and some Nvidia ck804 onboard sound.

Oops, I just realized I meant to say "Hardy beta".

---

### Post by phyrewall on 2008-03-21
Had the same problem, but I have full sound now that I did a clean install...

---

### Post by fadastic on 2008-03-22
Yeah, I don't know about doing a clean install considering I have all this media and settings I'd like to keep.

---

### Post by fadastic on 2008-03-22
By the way, here is what the error message states when I first click on the volume control:

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

---

