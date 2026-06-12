---
title: "MIDI Keyboard Recommendations?"
date: 2006-11-06
forum: Multimedia &amp; Video
---

### Post by coder_ on 2006-11-06
Hello!

I'm wondering if anyone has suggestions for what MIDI keyboard to buy?
I'd like one that is proven to work, and that is a moderate price.  I'm looking towards the lower end of the spectrum.

**Some ones I've looked at:**
[http://www.m-audio.com/products/en_us/MAudioO2-main.html](http://www.m-audio.com/products/en_us/MAudioO2-main.html)
[http://www.m-audio.com/products/en_us/eKeys37-main.html](http://www.m-audio.com/products/en_us/eKeys37-main.html)
[http://www.m-audio.com/products/en_us/Keystation49e-main.html](http://www.m-audio.com/products/en_us/Keystation49e-main.html)
[http://www.m-audio.com/products/en_us/Oxygen8v2-main.html](http://www.m-audio.com/products/en_us/Oxygen8v2-main.html)

Also, what application in Linux would I use to record what I play as through the MIDI keyboard?  And also, is it possible to set the midi keyboard up to send it's MIDI signals to Zynaddsubfx in JACK, like I can the VKeyBd software for realtime playing?  I'd like to jam along with some tracks and maybe record them in Ardour or something if I can get that to work.

Thanks for your help. :)

---

### Post by dolson on 2006-11-07
Having just gone through this, I am happy with my gamble purchase of E-mu Xboard49. Google it. It works in Ubuntu plug-n-play, no firmware loading, etc. Has aftertouch and 16 assignable knobs. USB-powered (or battery or AC if you don't use it with a PC). Just my recommendation. When I plug it in, it appears in the QjackCtl Patchbay just like VKeyBd does.

To answer your other question, you can use seq24, rosegarden, muse, etc. to compose MIDI tracks with your MIDI keyboard (or VKeyBd).

[IMG]http://www.sound7.be/Material/xboard49.jpg[/IMG]

---

### Post by KoRnholio on 2006-11-07
The Maudio Keystation 88es works perfectly for me (plug and play).

---

### Post by coder_ on 2006-11-07
I'd love an 88 key, but I don't have the moola for it.  The EMU one looks nice and a good price.  Thanks for the suggestions guys. :)  I really appreciate it. :)

*One more question*:  How easy is it to set up the knobs on the keyboard to adjust stuff like Zynaddsubfx or some parameters in a program for live performance?  How would you go about doing that?

Thanks in advance, and thanks for the help so far. :)  I'm really looking forward to getting one of these :D

---

### Post by 23meg on 2006-11-08
I'll second the Emu Xboard series, they're great value for money. Aftertouch, full weighted keys and velocity curves aren't features you usually find in that price range, and they have high build quality as well.

---

### Post by mo79 on 2006-11-08
Anyone know how to get an M-Audio Oxygen8 working, by any chance?

---

### Post by coder_ on 2006-11-08
By the way, anyone got any recommendations for a sound card with more than two input jacks?  :P   In a good price range please, as I'm looking to receive these for Christmas.

I'd like to have my friends jam along with me you know ;)

Thanks in advance, and it looks like I'll try to go with the Emu XBoard.  :)

---

### Post by dolson on 2006-11-09
coder_, your question about setting the knobs - it's not hard. I can't remember exactly off hand, since I don't reassign them often, but it's easy. The little book tells you how. You can store a bunch of presets too, so you can have one for zynaddsubfx, one for ams, etc etc. I think there are 10 or 16 or something like that (not sure the exact number off hand, but it's enough for me for sure). You can get a smaller board, and a bigger board or two as well. The 49 was in my price range and big enough to cover a few octaves. :)

---

### Post by CadetD on 2006-11-11
A great keyboard especially for Linux is the M-Audion Keystation Pro 88.
It's a USB 88-weighted key.

---

### Post by subluid on 2006-11-15
by the way, CME UF6
[http://www.cme-pro.com/products-list/product-uf.html](http://www.cme-pro.com/products-list/product-uf.html)
works plug and play as well.

zynaddsubfx has some default GM controllers assigned to parameters listed here:
[http://zynaddsubfx.sourceforge.net/doc_3.html](http://zynaddsubfx.sourceforge.net/doc_3.html)
i don't know if they can be changed, but it works as soon as connected directly or via a sequencer (seq24 is great and it records all midi-controller-events!).

Ardour is midi-controllable as well, just shift-middle-click on the respective fader and then move the midi controller you wish to assign.

the most flexible i found yet is ams. load a patch like bass.ams, open view -> control center from the menu, move a midi knob and assign it to ANY parameter of ANY module or LADSPA-plugin - having for instance cutoff freq., envelopes and some effects midi-controlled while playing is quite the best.

enjoy

---

### Post by GorArn on 2008-01-11
Anyone having positive experiences with a CME M-Key (49 keys, usb-midi, not very expensive)? I purchased such a thing before christmas and it's not plug and play. I've struggled with it since then. It is "recognised" as some Philips device and the system reports errors when probing for its functionality.

---

### Post by Pocadotty on 2008-01-18
as others have said E-MU Xboards are great... I just picked up a 25 key one.  Plug and play with Ubuntu 7.10, works well and can also be used as a midi-through via USB... if your sound card doesn't have midi.

Guitar center has the Xboard 25 and 49 on clearance for 80$ and 90$ respectively this month... So I had to get one... Awesome value!

---

