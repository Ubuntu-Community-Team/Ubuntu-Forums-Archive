---
title: "How to setup my MIDI keyboard to play piano?"
date: 2010-06-05
forum: Multimedia Software
---

### Post by vollucris on 2010-06-05
Hi!

I just switched to Ubuntu 10.04 and I'm looking for a way to be able to play piano with my M-audio Keystation 88es keyboard.
In Windows I use the amazing Synthogy Ivory piano sounds. Is there anything similar in linux?

Plus how do I set everything up? I followed different instructions on how to setup Jack to make it work and it can see the keyboard but I wasn't able to get any sound out of it.

My computer has the Asus built-in sound card and I also have a separate M-audio Audiophile 192 sound card.

Please help, I really want to use Ubuntu and I want to continue playing my piano!

Thanks,
Cris

---

### Post by Breambutt on 2010-06-06
A picture says more... and so forth, so I hope this helps:

[http://www.nbl.fi/~nbl4321/images/jack01.jpg](http://www.nbl.fi/~nbl4321/images/jack01.jpg)
[http://www.nbl.fi/~nbl4321/images/jack02.jpg](http://www.nbl.fi/~nbl4321/images/jack02.jpg)

That's with qjackctl, in case you're running jackd from terminal. You can also create ins and outs for more peculiar routing by running alsa_in and alsa_out with parameters of your choosing in terminal while jack is running.

And last, I don't know about those piano softs you mentioned, but you can run most of any VSTis in Linux too. There's also a VST for dummies ensemble "guide" I made for a couple of friends somewhere over there.

---

